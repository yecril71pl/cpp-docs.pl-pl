---
title: 'Instrukcje: interfejs między wyjątkowym i niewyjątkowym kodem'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
ms.openlocfilehash: 88dacda9b20f351eb67dde24a8335bdcbba27dd3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187702"
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>Instrukcje: interfejs między wyjątkowym i niewyjątkowym kodem

W tym artykule opisano, jak zaimplementować spójną obsługę wyjątków w module języka C++, a także jak przetłumaczyć te wyjątki na i z kodów błędów na granicach wyjątków.

Czasami moduł C++ ma interfejs z kodem, który nie używa wyjątków (kod niewyjątkowy). Taki interfejs jest znany jako *granica wyjątku*. Na przykład możesz chcieć wywołać funkcję Win32 `CreateFile` w programie języka C++. `CreateFile`nie zgłasza wyjątków; Zamiast tego ustawia kody błędów, które mogą być pobierane przez `GetLastError` funkcję. Jeśli Twój program w języku C++ nie jest prosty, prawdopodobnie wolisz mieć spójne zasady obsługi błędów oparte na wyjątkach. Prawdopodobnie nie chcesz porzucać wyjątków tylko z powodu interfejsu z niewyjątkowym kodem i nie chcesz mieszać zasad błędów opartych na wyjątkach i nieopartych na wyjątkach w module języka C++.

## <a name="calling-non-exceptional-functions-from-c"></a>Wywoływanie niewyjątkowych funkcji z C++

Gdy wywołujesz niewyjątkową funkcję z C++, pomysłem jest Zawijanie tej funkcji w funkcji języka C++, która wykrywa wszelkie błędy, a następnie może zgłaszać wyjątek. Podczas projektowania takiej funkcji otoki należy najpierw zdecydować, jaki typ gwarancji wyjątku należy podać: nie-throw, Strong lub Basic. Następnie Zaprojektuj funkcję tak, aby wszystkie zasoby, na przykład dojścia do plików, były prawidłowo wydane, jeśli wystąpi wyjątek. Zazwyczaj oznacza to, że do własnych zasobów można używać inteligentnych wskaźników lub podobnych menedżerów zasobów. Aby uzyskać więcej informacji na temat zagadnień związanych z projektowaniem, zobacz [How to: Design for Exception Safety](how-to-design-for-exception-safety.md).

### <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono funkcje języka C++, które używają Win32 `CreateFile` i `ReadFile` Functions wewnętrznie do otwierania i odczytywania dwóch plików.  `File`Klasa jest otoką inicjującą (RAII) do obsługi plików. Jego Konstruktor wykrywa warunek "nie znaleziono pliku" i zgłasza wyjątek w celu propagowania błędu w górę stosu wywołań modułu języka C++ (w tym przykładzie `main()` Funkcja). Jeśli wyjątek jest zgłaszany, gdy `File` obiekt jest w pełni skonstruowany, destruktor automatycznie wywołuje `CloseHandle` do zwolnienia dojścia do pliku. (Jeśli wolisz, możesz użyć klasy Active Template Library (ATL) `CHandle` w tym samym przeznaczeniu lub w `unique_ptr` połączeniu z niestandardowym usuwaniem). Funkcje, które wywołują interfejsy API Win32 i CRT, wykrywają błędy, a następnie generują wyjątki C++ przy użyciu funkcji zdefiniowanej lokalnie `ThrowLastErrorIf` , która z kolei używa `Win32Exception` klasy pochodzącej od `runtime_error` klasy. Wszystkie funkcje w tym przykładzie zapewniają silną gwarancję wyjątku; Jeśli w dowolnym momencie w tych funkcjach wystąpi wyjątek, żadne zasoby nie są wyciekami i nie jest modyfikowany żaden stan programu.

```cpp
// compile with: /EHsc
#include <Windows.h>
#include <stdlib.h>
#include <vector>
#include <iostream>
#include <string>
#include <limits>
#include <stdexcept>

using namespace std;

string FormatErrorMessage(DWORD error, const string& msg)
{
    static const int BUFFERLENGTH = 1024;
    vector<char> buf(BUFFERLENGTH);
    FormatMessageA(FORMAT_MESSAGE_FROM_SYSTEM, 0, error, 0, buf.data(),
        BUFFERLENGTH - 1, 0);
    return string(buf.data()) + "   ("  + msg  + ")";
}

class Win32Exception : public runtime_error
{
private:
    DWORD m_error;
public:
    Win32Exception(DWORD error, const string& msg)
        : runtime_error(FormatErrorMessage(error, msg)), m_error(error) { }

    DWORD GetErrorCode() const { return m_error; }
};

void ThrowLastErrorIf(bool expression, const string& msg)
{
    if (expression) {
        throw Win32Exception(GetLastError(), msg);
    }
}

class File
{
private:
    HANDLE m_handle;

    // Declared but not defined, to avoid double closing.
    File& operator=(const File&);
    File(const File&);
public:
    explicit File(const string& filename)
    {
        m_handle = CreateFileA(filename.c_str(), GENERIC_READ, FILE_SHARE_READ,
            nullptr, OPEN_EXISTING, FILE_ATTRIBUTE_READONLY, nullptr);
        ThrowLastErrorIf(m_handle == INVALID_HANDLE_VALUE,
            "CreateFile call failed on file named " + filename);
    }

    ~File() { CloseHandle(m_handle); }

    HANDLE GetHandle() { return m_handle; }
};

size_t GetFileSizeSafe(const string& filename)
{
    File fobj(filename);
    LARGE_INTEGER filesize;

    BOOL result = GetFileSizeEx(fobj.GetHandle(), &filesize);
    ThrowLastErrorIf(result == FALSE, "GetFileSizeEx failed: " + filename);

    if (filesize.QuadPart < (numeric_limits<size_t>::max)()) {
        return filesize.QuadPart;
    } else {
        throw;
    }
}

vector<char> ReadFileVector(const string& filename)
{
    File fobj(filename);
    size_t filesize = GetFileSizeSafe(filename);
    DWORD bytesRead = 0;

    vector<char> readbuffer(filesize);

    BOOL result = ReadFile(fobj.GetHandle(), readbuffer.data(), readbuffer.size(),
        &bytesRead, nullptr);
    ThrowLastErrorIf(result == FALSE, "ReadFile failed: " + filename);

    cout << filename << " file size: " << filesize << ", bytesRead: "
        << bytesRead << endl;

    return readbuffer;
}

bool IsFileDiff(const string& filename1, const string& filename2)
{
    return ReadFileVector(filename1) != ReadFileVector(filename2);
}

#include <iomanip>

int main ( int argc, char* argv[] )
{
    string filename1("file1.txt");
    string filename2("file2.txt");

    try
    {
        if(argc > 2) {
            filename1 = argv[1];
            filename2 = argv[2];
        }

        cout << "Using file names " << filename1 << " and " << filename2 << endl;

        if (IsFileDiff(filename1, filename2)) {
            cout << "+++ Files are different." << endl;
        } else {
            cout<< "=== Files match." << endl;
        }
    }
    catch(const Win32Exception& e)
    {
        ios state(nullptr);
        state.copyfmt(cout);
        cout << e.what() << endl;
        cout << "Error code: 0x" << hex << uppercase << setw(8) << setfill('0')
            << e.GetErrorCode() << endl;
        cout.copyfmt(state); // restore previous formatting
    }
}
```

## <a name="calling-exceptional-code-from-non-exceptional-code"></a>Wywoływanie wyjątkowego kodu z kodu niewyjątkowego

Funkcje języka C++, które są zadeklarowane jako "extern C", mogą być wywoływane przez programy C. Serwery C++ COM mogą być używane przez kod zapisany w dowolnej wielu różnych językach. W przypadku zaimplementowania funkcji publicznych obsługujących wyjątki w języku C++ do wywołania przez kod niewyjątkowy, funkcja C++ nie może zezwalać na żadne wyjątki do propagacji z powrotem do obiektu wywołującego. W związku z tym, funkcja języka C++ musi zwrócić uwagę na każdy wyjątek, który wie, jak obsłużyć i, w razie potrzeby, przekonwertować wyjątek na kod błędu, który jest rozpoznawany przez wywołującego. Jeśli nie wszystkie potencjalne wyjątki są znane, funkcja C++ powinna mieć `catch(...)` blok jako ostatnią procedurę obsługi. W takim przypadku najlepszym rozwiązaniem jest zgłoszenie błędu krytycznego do obiektu wywołującego, ponieważ program może znajdować się w nieznanym stanie.

W poniższym przykładzie pokazano funkcję, która zakłada, że każdy wyjątek, który może zostać wygenerowany jest Win32exception lub typ wyjątku pochodzący z `std::exception` . Funkcja przechwytuje dowolny wyjątek tych typów i propaguje informacje o błędzie jako kod błędu Win32 do obiektu wywołującego.

```cpp
BOOL DiffFiles2(const string& file1, const string& file2)
{
    try
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return FALSE;
        }
        return TRUE;
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }

    catch(std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return FALSE;
}
```

W przypadku konwersji z wyjątków na kody błędów, jeden potencjalny problem występuje, że kody błędów często nie zawierają bogatej informacji, które mogą być przechowywane przez wyjątek. Aby rozwiązać ten problem, można dostarczyć **`catch`** blok dla każdego określonego typu wyjątku, który może zostać wygenerowany, i wykonać rejestrowanie, aby zarejestrować szczegóły wyjątku przed przekonwertowaniem go na kod błędu. Takie podejście może stworzyć wiele powtórzeń kodu, jeśli wiele funkcji używa tego samego zestawu **`catch`** bloków. Dobrym sposobem uniknięcia powtarzania kodu jest Refaktoryzacja tych bloków w jedną funkcję narzędzia prywatnego, która implementuje **`try`** **`catch`** bloki i i akceptuje obiekt Function, który jest wywoływany w **`try`** bloku. W każdej funkcji publicznej Przekaż kod do funkcji narzędzia jako wyrażenie lambda.

```cpp
template<typename Func>
bool Win32ExceptionBoundary(Func&& f)
{
    try
    {
        return f();
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }
    catch(const std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return false;
}
```

Poniższy przykład pokazuje, jak napisać wyrażenie lambda definiujące Funktor. Gdy element Funktor jest zdefiniowany jako "inline" przy użyciu wyrażenia lambda, często jest to łatwiejsze do odczytania niż w przypadku, gdy został on zapisany jako nazwany obiekt funkcji.

```cpp
bool DiffFiles3(const string& file1, const string& file2)
{
    return Win32ExceptionBoundary([&]() -> bool
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return false;
        }
        return true;
    });
}
```

Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](lambda-expressions-in-cpp.md).

## <a name="see-also"></a>Zobacz także

[Nowoczesne najlepsze rozwiązania w języku C++ dotyczące wyjątków i obsługi błędów](errors-and-exception-handling-modern-cpp.md)<br/>
[Instrukcje: projektowanie pod kątem bezpieczeństwa wyjątków](how-to-design-for-exception-safety.md)<br/>

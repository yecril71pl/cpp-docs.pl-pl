---
title: 'Porady: interfejs między kodem obsługi wyjątków a innym kodem | Dokumentacja firmy Microsoft'
ms.custom: how-to
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74805c7ecd4b4ecef71d8ac1358fd6c2014e27d5
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940121"
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>Porady: interfejs między kodem obsługi wyjątków a innym kodem
W tym artykule opisano, jak wdrożyć spójne obsługi wyjątków w module języka C++, a także tłumaczenie tych wyjątków do i z kodów błędów na granicach wyjątków.  
  
 Czasami moduł C++ ma interfejs z kodem, który nie używa wyjątków (kod bez wyjątków). Ten interfejs jest znany jako *granica wyjątku*. Na przykład, można wywołać funkcję Win32 `CreateFile` w programach języka C++. `CreateFile` nie wyrzuca wyjątków; zamian ustawia kody błędów, które mogą być pobierane według `GetLastError` funkcji. Jeśli program w języku C++ jest trywialny, następnie w nim prawdopodobnie chcesz mieć spójną politykę obsługi błędów opartą na wyjątkach. I prawdopodobnie nie chcesz porzucić wyjątków tylko dlatego, że interfejs z kodem niewyjątkowym i nie chcesz mieszać polityk błędów opartą na wyjątkach, a systemem wyjątku w C++ module.  
  
## <a name="calling-non-exceptional-functions-from-c"></a>Wywoływanie funkcji Niewyjątkowych z języka C++  
 Po wywołaniu funkcji niewyjątkowych z języka C++, ideą jest zwinięcie tej funkcji w funkcji języka C++, który wykrywa błędy i ewentualnie zgłasza wyjątek. Podczas projektowania takiej funkcji otoku, najpierw zdecyduj jaki rodzaj gwarancji wyjątek zapewnić: nie wyrzucający, silny lub podstawowy. Po drugie zaprojektuj własną funkcję tak, aby wszystkie zasoby, na przykład, dojścia do plików, są poprawnie zwolnione jeśli zostanie zgłoszony wyjątek. Zazwyczaj oznacza to, że używasz inteligentnych wskaźników lub podobne menedżerów zasobów do własnych zasobów. Aby uzyskać więcej informacji na temat zagadnień projektowych, zobacz [porady: Projektowanie pod kątem bezpieczeństwa wyjątków](../cpp/how-to-design-for-exception-safety.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono funkcje C++, która używa Win32 `CreateFile` i `ReadFile` funkcje wewnętrznie, aby otworzyć i przeczytać dwa pliki.  `File` Klasa jest pozyskiwaniem zasobów do inicjowania (RAII) otoki dla dojścia do plików. Jego Konstruktor wykryje warunek "nie można odnaleźć pliku" i zgłasza wyjątek do propagowania błędu w górę stosu wywołań modułu języka C++ (w tym przykładzie `main()` funkcji). Jeśli wyjątek jest zgłaszany po `File` object pełni skonstruowanym, destruktor automatycznie wywołuje `CloseHandle` aby zwolnić obsługę pliku. (Jeśli wolisz, możesz użyć Active Template Library (ATL) `CHandle` klasy, w tym samym celu lub `unique_ptr` wraz z niestandardowym narzędziem usuwania.) Funkcje, które wywołują funkcje API CRT i Win32 wykrywania błędów i następnie generują wyjątki C++ przy użyciu zdefiniowanej lokalnie `ThrowLastErrorIf` funkcji, która z kolei używa `Win32Exception` klasy pochodzące z `runtime_error` klasy. Wszystkie funkcje w tym przykładzie zapewniają gwarancję silnego wyjątku; Jeśli wyjątek jest zgłaszany w dowolnym momencie w tych funkcji, wyciek zasobów i żaden stan programu nie zostanie zmodyfikowany.  
  
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
            cout << "*** Files are different." << endl;  
        } else {  
            cout<< "*** Files match." << endl;  
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
  
## <a name="calling-exceptional-code-from-non-exceptional-code"></a>Wywołanie kodu wyjątkowego z kodu Niewyjątkowego  
 Funkcje języka C++, które są zadeklarowane jako "extern C" mogą być wywoływane przez programy c. Serwery C++ COM mogą być używane przez kod napisany w dowolnej liczbie różnych języków. Podczas implementowania funkcji publicznych obsługujących wyjątek w języku C++ do wywołania przez kod bez wyjątków, funkcja C++ nie może dopuszczać wyjątków do propagowania obiektu wywołującego. W związku z tym funkcja C++ musi w szczególności złapać każdy wyjątek, który wie, jak obsługiwać i, jeśli to stosowne, przekonwertować wyjątek kodu błędu, który rozumie obiekt wywołujący. Jeśli nie wszystkie potencjalne wyjątki są znane, funkcja C++ powinna mieć `catch(...)` bloku jako ostatnią procedurę obsługi. W takim przypadku najlepiej zgłosić błąd krytyczny do obiektu wywołującego, ponieważ program może znajdować się w nieznanym stanie.  
  
 W poniższym przykładzie pokazano funkcję, która zakłada, że każdy wyjątek, który może zostać wygenerowany jest Win32Exception lub jest typem wyjątku pochodzącym z `std::exception`. Funkcja przechwytuje wszystkie wyjątki tych typów i propaguje informacje o błędzie jako kodzie błędu Win32 do obiektu wywołującego.  
  
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
  
 Podczas konwersji z wyjątków do kodów błędów jeden potencjalny problem jest, że kody błędów często nie zawierają bogactwa informacji, które mogą być przechowywane w drodze wyjątku. Aby rozwiązać ten problem, możesz podać **catch** blok dla każdego typu określonego wyjątku, który może zostać wygenerowany i wykonać logowanie do rejestrowania szczegółów wyjątku, przed konwersją do kodu błędu. Takie podejście może utworzyć wiele powtarzających się kodów, jeśli wiele funkcji używa tego samego zestawu **catch** bloków. Dobrym sposobem na uniknięcie powtórzenia kodu jest Refaktoryzacja tych bloków w jedną funkcję narzędzi prywatnych, który implementuje **spróbuj** i **catch** blokuje i akceptuje obiekt funkcji, która jest wywoływana w **spróbuj** bloku. W każdej funkcji publicznej należy przekazać kod do funkcji narzędzia jako wyrażenie lambda.  
  
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
  
 Poniższy przykład pokazuje, jak napisać wyrażenie lambda, które definiuje funkcję. Gdy teoria jest zdefiniowana "inline" przy użyciu wyrażenia lambda, często jest łatwiejsza do odczytania niż byłaby, jeśli zostałaby napisana jako obiekt o nazwie funkcji.  
  
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
  
 Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy w obsłudze wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Instrukcje: projektowanie pod kątem bezpieczeństwa wyjątków](../cpp/how-to-design-for-exception-safety.md)
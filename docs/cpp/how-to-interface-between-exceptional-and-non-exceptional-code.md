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
ms.openlocfilehash: f2cf2216ba75912520f744f0f0331a50520aa895
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>Porady: interfejs między kodem obsługi wyjątków a innym kodem
W tym artykule opisano sposobu wdrażania spójne obsługi wyjątków w module języka C++, a także tłumaczenie tych wyjątków do i z kodów błędów na granicach wyjątek.  
  
 Czasami ma moduł C++ do interfejsu z kodem, który nie używa wyjątków (z systemem innym niż wyjątkowych kodu). Takiego interfejsu jest nazywany *granic wyjątek*. Na przykład można wywołać funkcji Win32 `CreateFile` programu C++. `CreateFile` nie zgłaszają wyjątki; Zamiast tego ustawia kody błędów, które mogą zostać pobrane przez `GetLastError` funkcji. W przypadku nieuproszczony program w języku C++, następnie w nim prawdopodobnie preferowane spójne wyjątek na podstawie zasad obsługi błędów. I prawdopodobnie nie chcesz abandon wyjątki tak, ponieważ połączenie z innym kodem kodu i nie chcesz mieszać zasady na podstawie wyjątku i systemem wyjątek Błąd w module języka C++.  
  
## <a name="calling-non-exceptional-functions-from-c"></a>Wywoływanie funkcji innym kodem z C++  
 Podczas wywoływania funkcji innym kodem z C++, będzie zawijany tej funkcji w funkcji języka C++, która wykrywa wszystkie błędy i prawdopodobnie zgłasza wyjątek. Podczas projektowania funkcja otoki, najpierw wybierz typ wyjątku gwarancji, aby zapewnić: throw nie, silne lub podstawowa. Po drugie projektowanie funkcji tak, aby wszystkie zasoby, na przykład dojść do plików, są zwalniane poprawnie, jeśli wyjątek. Zazwyczaj oznacza to, użyj wskaźniki inteligentne lub podobne menedżerowie zasobów do własnych zasobów. Aby uzyskać więcej informacji na temat projektowania, zobacz [porady: Projektowanie pod kątem bezpieczeństwa wyjątków](../cpp/how-to-design-for-exception-safety.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano funkcje języka C++, które używają środowiska Win32 `CreateFile` i `ReadFile` funkcji wewnętrznie otwierać i odczytywać pliki dwa.  `File` Klasy jest nabywania zasobów otoki inicjowania (RAII) dla dojścia do plików. Jego konstruktora wykryje warunek "nie można odnaleźć pliku" i zgłasza wyjątek propagację błąd górę stosu wywołań modułu C++ (w tym przykładzie `main()` funkcji). Jeśli wyjątek jest zgłaszany po `File` obiektu jest dokończony, destruktor automatycznie wywołuje `CloseHandle` zwolnienia dojście do pliku. (Jeśli wolisz, możesz użyć Active Template Library (ATL) `CHandle` klasy w tym samym celu lub `unique_ptr` wraz z niestandardowych deleter.) Funkcje wywołujące Win32 i CRT interfejsy API wykrywania błędów i następnie zgłaszają wyjątki C++ za pomocą zdefiniowane lokalnie `ThrowLastErrorIf` funkcji, który z kolei używa `Win32Exception` klasę pochodną `runtime_error` klasy. Wszystkie funkcje w tym przykładzie gwarantować silne wyjątek; Jeśli w dowolnym momencie w tych funkcji jest zgłaszany wyjątek, żadne zasoby są ujawnione i Państwa program nie jest modyfikowany.  
  
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
  
## <a name="calling-exceptional-code-from-non-exceptional-code"></a>Wywoływanie kodu wyjątkowych z innym kodem kodu  
 Funkcje języka C++, które są zadeklarowane jako "extern C" może być wywoływany przez C — programy. Serwery C++ COM mogą być używane przez kod napisany w jednym z kilku różnych języków. Po zaimplementowaniu publicznego funkcje obsługą wyjątków języka C++ ma zostać wywołana przez kod innym kodem C++ funkcji nie może dopuszczać wszelkie wyjątki obejmie wywołującego. W związku z tym funkcja C++ musi w szczególności catch co wyjątek, który potrafi obsłużyć, i w razie potrzeby przekonwertować wyjątek obsługującą wywołującego kod błędu. Jeśli nie wszystkie potencjalne wyjątki są znane, funkcja C++ powinien mieć `catch(...)` bloku jako ostatni obsługi. W takim przypadku najlepiej zgłoszenia krytyczny błąd do wywołującego, ponieważ program może być w nieznanym stanie.  
  
 Poniższy przykład przedstawia funkcję, która zakłada, że każdy wyjątek, który może zostać wygenerowany win32exception — lub typ wyjątku pochodzących z `std::exception`. Funkcja przechwytuje wszystkie wyjątki tego typu i propaguje informacje o błędzie jako kod błędu Win32 do obiektu wywołującego.  
  
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
  
 Podczas konwertowania z wyjątków kody błędów jednym potencjalnych problemów jest czy kody błędów często nie mogą zawierać siłę informacji, które mogą być przechowywane przez wyjątek. Aby rozwiązać ten problem, można zapewnić `catch` bloku dla każdego typu określony wyjątek, który może zostać zgłoszone, a następnie wykonać rejestrowania, aby zarejestrować szczegóły wyjątku, zanim zostanie przekonwertowane na kod błędu. Tej metody można utworzyć kod aktualnymi użycie wielu funkcji wszystkie ten sam zestaw `catch` bloków. Sposobem uniknięcia powtórzenia kodu jest refaktoryzacji te bloki w jednej funkcji prywatnej narzędzie implementujący `try` i `catch` blokuje i akceptuje obiekt funkcji, które jest wywoływane w `try` bloku. W każdej funkcji publiczny należy przekazać kod funkcji narzędzia jako wyrażenia lambda.  
  
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
  
 Poniższy przykład przedstawia sposób zapisania wyrażenia lambda, który definiuje obiekt. Gdy obiekt jest zdefiniowano "w tekście" za pomocą wyrażenia lambda, często jest bardziej czytelny byłoby, jeśli były zapisywane jako obiekt o nazwie funkcji.  
  
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
  
 Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy w obsłudze wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Instrukcje: projektowanie pod kątem bezpieczeństwa wyjątków](../cpp/how-to-design-for-exception-safety.md)
---
title: Transport wyjątków między wątkami | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- std::current_exception
- transporting exceptions between threads
- std::copy_exception
- exception_ptr
- std::exception_ptr
- std::rethrow_exception
- current_exception
- transport exceptions between threads
- copy_exception
- rethrow_exception
- move exceptions between threads
ms.assetid: 5c95d57b-acf5-491f-8122-57c5df0edd98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61847500e9e4fbcfc0912e51afe599ed31601ec2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="transporting-exceptions-between-threads"></a>transport wyjątków między wątkami
Visual C++ obsługuje *transportowania wyjątek* z jednego wątku na inny. Transport wyjątków umożliwia przechwytywanie wyjątków w jednym wątku, a następnie powodowanie, aby były generowane w innym wątku. Na przykład, możesz użyć tej funkcji do pisania aplikacji wielowątkowych, gdzie wątek główny obsługuje wszystkie wyjątki generowane przez pomocnicze wątki. Transport wyjątków jest przydatny głównie dla deweloperów, którzy tworzą biblioteki lub systemy programowania równoległego. Aby zaimplementować transportu wyjątki, zapewnia Visual C++ [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) typu i [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception), i [make_ exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
namespace std   
{  
   typedef unspecified exception_ptr;   
   exception_ptr current_exception();  
   void rethrow_exception(exception_ptr p);  
   template<class E>   
       exception_ptr make_exception_ptr(E e) noexcept;  
}  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`unspecified`|Nieokreślony wewnętrzny klasy, która służy do implementowania `exception_ptr` typu.|  
|`p`|`exception_ptr` Obiekt, który odwołuje się do wyjątku.|  
|`E`|Klasa, która reprezentuje wyjątek.|  
|`e`|Wystąpienia parametru `E` klasy.|  
  
## <a name="return-value"></a>Wartość zwracana  
 `current_exception` Funkcja zwraca `exception_ptr` obiektu, który odwołuje się do wyjątku, który jest obecnie w toku. Jeśli żaden wyjątek jest w toku, funkcja zwraca `exception_ptr` obiekt, który nie jest skojarzony z żadnym wyjątku.  
  
 `make_exception_ptr` Funkcja zwraca `exception_ptr` obiekt, który odwołuje się określony przez wyjątek `e` parametru.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="scenario"></a>Scenariusz  
 Wyobraź sobie, że chcesz utworzyć aplikację, która może być skalowana, aby obsłużyć zmienną ilość pracy. Aby osiągnąć ten cel, projektujesz aplikację wielowątkową, gdzie wstępny, podstawowy wątek tworzy tyle wątków pomocniczych, ile potrzebuje, aby wykonać zadanie. Pomocnicze wątki pomagają wątkowi głównemu zarządzać zasobami, równoważyć obciążenia, a także zwiększać wydajność. Dzięki rozłożeniu pracy, aplikacja wielowątkowa działa lepiej niż aplikacja jednowątkowa.  
  
 Jednak jeśli wątek pomocniczy zgłasza wyjątek, wskazane jest, aby watek główny go obsłużył. To dlatego, że chcesz, aby aplikacja obsługiwała wyjątki w sposób spójny, jednolity, bez względu na liczbę wątków pomocniczych.  
  
## <a name="solution"></a>Rozwiązanie  
 Aby obsłużyć poprzedni scenariusz, standard C++ obsługuje transportowanie wyjątków pomiędzy wątkami. Jeśli wątek pomocniczy zgłasza wyjątek, staje się ten wyjątek *bieżący wyjątek*. Analogicznie do rzeczywistych bieżący wyjątek jest określany jako *transmitowane*. Bieżący wyjątek jest w locie od czasu, kiedy jest generowany, aż do momentu, gdy zostanie zwrócony przez kod obsługi wyjątków, który go przechwycił.  
  
 Wątek pomocniczy można przechwycić bieżącego wyjątku w `catch` zablokować, a następnie wywołać `current_exception` funkcji do przechowywania wyjątek w `exception_ptr` obiektu. `exception_ptr` Obiekt musi być dostępny do dodatkowej wątku i podstawowy wątku. Na przykład `exception_ptr` obiekt może mieć zmiennej globalnej, do których dostęp jest kontrolowany przez obiektu mutex. Termin *transportu wyjątek* oznacza, że wystąpił wyjątek w jeden wątek może zostać przekonwertowany na formularz, który jest dostępny przez inny wątek.  
  
 Następnie wywołuje podstawowy wątku `rethrow_exception` funkcji, która umożliwia wyodrębnianie i następnie zgłasza wyjątek z `exception_ptr` obiektu. Wygenerowany wyjątek staje się bieżącym wyjątkiem w wątku głównym. Oznacza to, że wyjątek wygląda tak, jakby pochodził z wątku głównego.  
  
 Na koniec podstawowy wątku można przechwycić bieżącego wyjątku w `catch` zablokować, a następnie go przetworzyć lub zgłosić go do nowszej obsługi wyjątków poziomu. Lub wątek główny może zignorować wyjątek i pozwolić zakończyć proces.  
  
 Większość aplikacji nie musi transportować wyjątków między wątkami. Jednak ta funkcja jest przydatna w systemach przetwarzania równoległego, ponieważ system może podzielić pracę pomiędzy wątki pomocnicze, procesory lub rdzenie. W środowisku przetwarzania równoległego pojedynczy, wyspecjalizowany wątek może obsługiwać wszystkie wyjątki z pomocniczych wątków i może stanowić spójny model obsługi wyjątków dla innych aplikacji.  
  
 Aby uzyskać więcej informacji o propozycji komitetu standardów C++, znajdź w Internecie dokument o numerze N2179 pod tytułem „Language Support for Transporting Exceptions between Threads” (Obsługa języka dla transportu wyjątków między wątkami).  
  
## <a name="exception-handling-models-and-compiler-options"></a>Opcje kompilatora i modele obsługi wyjątków  
 Model obsługi wyjątków aplikacji określa, czy można przechwycić i transportować wyjątek. Visual C++ obsługuje trzy modele, które mogą obsługiwać wyjątki C++, obsługę wyjątków strukturalnych (SEH) i wyjątki środowiska uruchomieniowego języka wspólnego (CLR). Użyj [/EH](../build/reference/eh-exception-handling-model.md) i [/CLR](../build/reference/clr-common-language-runtime-compilation.md) opcji kompilatora, aby określić model obsługi wyjątków aplikacji.  
  
 Tylko następujące połączenie opcji kompilatora i instrukcji programowania może transportować wyjątek. Inne połączenia nie mogą przechwytywać wyjątków lub mogą je przechwytywać, ale nie transportować.  
  
-   **/Eha** — opcja kompilatora i `catch` instrukcji za przesyłanie wyjątków SEH i C++.  
  
-   **/Eha**, **/EHS**, i **/ehsc** — opcje kompilatora i `catch` instrukcji za przesyłanie wyjątków języka C++.  
  
-   **/CLR** lub **/CLR: pure** — opcja kompilatora i `catch` instrukcji za przesyłanie wyjątków języka C++. **/CLR** — opcje kompilatora oznaczać specyfikacji **/eha** opcji. Należy zauważyć, że kompilator nie obsługuje transportowania wyjątków zarządzanych. Jest to spowodowane zarządzanych wyjątków, które są pochodnymi [klasy System.Exception](../standard-library/exception-class.md), są już obiekty, które można przenosić między wątkami przy użyciu funkcji languange plików wykonywalnych.  
  
    > [!IMPORTANT]
    >  Firma Microsoft zaleca, aby określić **/ehsc** — opcja kompilatora i catch tylko wyjątki C++. Naraża samodzielnie na zagrożenia bezpieczeństwa, jeśli używasz **/eha** lub **/CLR** — opcja kompilatora i **catch** instrukcji z wielokropkiem  *deklaracji wyjątku* (`catch(...)`). Prawdopodobnie zamierzasz używać `catch` instrukcji, aby przechwycić kilka określonych wyjątków. Jednak `catch(...)` instrukcji przechwytuje wyjątków wszystkie C++ i SEH, w tym nieoczekiwany te, które powinny być krytyczny. Jeśli zignorujesz lub źle obsłużysz nieoczekiwany wyjątek, złośliwy kod wykorzystać tę szansę do obejścia zabezpieczeń programu.  
  
## <a name="usage"></a>Użycie  
 W poniższych sekcjach opisano sposób transportu wyjątków przy użyciu `exception_ptr` typu i `current_exception`, `rethrow_exception`, i `make_exception_ptr` funkcji.  
  
### <a name="exceptionptr-type"></a>Typ exception_ptr  
 Użyj `exception_ptr` obiekt, aby odwoływać się do bieżącego wyjątku lub wystąpienie wyjątku określone przez użytkownika. W implementacji firmy Microsoft wyjątek jest reprezentowana przez [EXCEPTION_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082) struktury. Każdy `exception_ptr` obiektu zawiera pole odwołania wyjątek wskazujące kopię `EXCEPTION_RECORD` strukturę, która reprezentuje wyjątek.  
  
 Gdy zadeklarować `exception_ptr` zmiennej, zmienna nie jest skojarzony z żadnym wyjątku. To znaczy, że pole odwołania wyjątku ma wartość NULL. Takie `exception_ptr` nosi nazwę obiektu *null exception_ptr*.  
  
 Użyj `current_exception` lub `make_exception_ptr` przypisanie wyjątek `exception_ptr` obiektu. Po przypisaniu wyjątek `exception_ptr` zmiennej, odwołanie do zmiennej wyjątek pola wskazuje kopię wyjątek. Jeśli jest za mało pamięci, aby skopiować wyjątek, pole odwołania wyjątek wskazuje kopię [std::bad_alloc](../standard-library/bad-alloc-class.md) wyjątku. Jeśli `current_exception` lub `make_exception_ptr` funkcji nie można skopiować wyjątek dla innego powodu, wywołania funkcji [przerwanie](../c-runtime-library/reference/terminate-crt.md) funkcji, aby zamknąć bieżącego procesu.  
  
 Pomimo swojej nazwy `exception_ptr` obiektu sam nie jest wskaźnikiem. Nie podlega semantyka wskaźnika i nie można używać z dostęp do elementu członkowskiego wskaźnika (`->`) lub operatory pośredni (*). `exception_ptr` Obiekt nie ma publicznych elementów członkowskich danych ani funkcji elementów członkowskich.  
  
 **Porównania:**  
  
 Można użyć równości (`==`) i nie równości (`!=`) operatorów, aby porównać dwa `exception_ptr` obiektów. Operatory porównania nie wartość binarna (wzorca bitowego) `EXCEPTION_RECORD` struktur reprezentujących wyjątki. Zamiast tego operatory porównania adres w polu odwołania wyjątek `exception_ptr` obiektów. W rezultacie null `exception_ptr` i porównać jako równe wartości NULL.  
  
### <a name="currentexception-function"></a>Funkcja current_exception  
 Wywołanie `current_exception` działać w `catch` bloku. Jeśli wyjątek jest transmitowane i `catch` bloku można przechwytywać elementu exception, `current_exception` funkcja zwraca `exception_ptr` obiektu, który odwołuje się do wyjątku. W przeciwnym razie funkcja zwraca wartość null `exception_ptr` obiektu.  
  
 **Szczegóły:**  
  
 `current_exception` Funkcja przechwytuje wyjątek, który są przesyłane niezależnie od tego, czy `catch` określa instrukcji [deklaracji wyjątku](../cpp/try-throw-and-catch-statements-cpp.md) instrukcji.  
  
 Destruktor dla bieżącego wyjątku jest wywoływana po zakończeniu `catch` zablokować, jeśli nie ponownie Zgłoś wyjątek. Jednak nawet wtedy, gdy jest wywoływana `current_exception` działać w destruktor, funkcja zwraca `exception_ptr` obiektu, który odwołuje się do bieżącego wyjątku.  
  
 Kolejne wywołania `current_exception` funkcji powrotu `exception_ptr` obiekty, które odwołują się do różnych kopii bieżącego wyjątku. W związku z tym obiekty są porównane jako nierówne, ponieważ odnoszą się one do poszczególnych kopii, mimo że kopie mają tę samą wartość binarną.  
  
 **Wyjątki SEH:**  
  
 Jeśli używasz **/eha** — opcja kompilatora, można przechwytywać wyjątku SEH w C++ `catch` bloku. `current_exception` Funkcja zwraca `exception_ptr` obiektu, który odwołuje się do wyjątków SEH. I `rethrow_exception` funkcja wyrzuca wyjątki SEH, jeśli dzwonisz z thetransported `exception_ptr` obiektu jako jej argument.  
  
 `current_exception` Funkcja zwraca wartość null `exception_ptr` można wywołać w SEH `__finally` programu obsługi zakończenia, `__except` obsługi wyjątków lub `__except` wyrażenie filtru.  
  
 Transportowany wyjątek nie obsługuje wyjątków zagnieżdżonych. Wyjątek zagnieżdżony występuje, jeśli podczas obsługi wyjątku jest zgłaszany inny wyjątek. Jeśli catch wyjątku zagnieżdżonych, `EXCEPTION_RECORD.ExceptionRecord` element członkowski danych wskazuje łańcucha `EXCEPTION_RECORD` struktur, które opisują skojarzone wyjątków. `current_exception` Funkcji nie obsługuje zagnieżdżonych wyjątkami, ponieważ zwraca `exception_ptr` którego `ExceptionRecord` wyzerowanie jest element członkowski danych.  
  
 Jeśli catch wyjątku SEH, należy zarządzać pamięci odwołuje się żadnych wskaźnika w `EXCEPTION_RECORD.ExceptionInformation` danych elementu członkowskiego tablicy. Musi gwarantuje, że pamięć jest prawidłowy, okres istnienia odpowiadającego `exception_ptr` obiekt i że zostanie zwolniona pamięć podczas `exception_ptr` obiekt jest usunięty.  
  
 Można użyć funkcji tłumacza wyjątków strukturalnych (SE) wraz z funkcją transportu wyjątków. Jeśli wyjątek SEH jest translacja wyjątek C++, `current_exception` funkcja zwraca `exception_ptr` , która odwołuje się przetłumaczonego wyjątek zamiast oryginalnej wyjątków SEH. `rethrow_exception` Funkcja zwraca następnie przetłumaczonego wyjątek nie pierwotny wyjątek. Aby uzyskać więcej informacji na temat funkcji SE translatora zobacz [_set_se_translator —](../c-runtime-library/reference/set-se-translator.md).  
  
### <a name="rethrowexception-function"></a>Funkcja rethrow_exception  
 Po przechowywania zgłoszony wyjątek w `exception_ptr` obiekt podstawowy wątku można przetworzyć obiektu. W sieci podstawowej wątku wywołać `rethrow_exception` działają razem z `exception_ptr` obiektu jako jej argument. `rethrow_exception` Funkcja wyodrębnia wyjątku z `exception_ptr` obiekt, a następnie zgłasza wyjątek w kontekście podstawowy wątku. Jeśli `p` parametr `rethrow_exception` wartość null jest funkcja `exception_ptr`, funkcja zwraca [std::bad_exception](../standard-library/bad-exception-class.md).  
  
 Wyodrębniony wyjątek jest teraz wyjątkiem bieżącym w wątku podstawowym i można go obsłużyć, podobnie jak w przypadku innych wyjątków. Jeśli catch wyjątku, można go obsłużyć natychmiast lub przy użyciu `throw` instrukcji do wysyłania do wyższych obsługi wyjątków poziomu. W przeciwnym razie nic nie rób, niech domyślny program obsługi wyjątków systemu zakończy proces.  
  
### <a name="makeexceptionptr-function"></a>Funkcja make_exception_ptr  
 `make_exception_ptr` Funkcja przyjmuje wystąpienia klasy jako jej argument, a następnie zwraca `exception_ptr` odwołujący się tego wystąpienia. Zwykle, określ [klasy wyjątku](../standard-library/exception-class.md) obiektu jako argument `make_exception_ptr` działanie, mimo że dowolny obiekt klasy może być argumentem.  
  
 Wywoływanie `make_exception_ptr` funkcji jest odpowiednikiem Zgłaszanie wyjątku C++ przechwytywanie w `catch` bloku, a następnie wywołując `current_exception` funkcja zwracająca `exception_ptr` obiektu, który odwołuje się do wyjątku. Implementacja firmy Microsoft `make_exception_ptr` funkcja jest bardziej efektywne niż zgłaszanie, a następnie przechwytywanie wyjątku.  
  
 Zwykle nie wymaga aplikacji `make_exception_ptr` funkcji i firma Microsoft zniechęcić jej użycia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład transportuje standardowy wyjątek C++ i niestandardowy wyjątek C++ z jednego wątku do innego.  
  
```  
// transport_exception.cpp  
// compile with: /EHsc /MD  
#include <windows.h>  
#include <stdio.h>   
#include <exception>  
#include <stdexcept>  
  
using namespace std;  
  
// Define thread-specific information.  
#define THREADCOUNT 2  
exception_ptr aException[THREADCOUNT];   
int           aArg[THREADCOUNT];  
  
DWORD WINAPI ThrowExceptions( LPVOID );   
  
// Specify a user-defined, custom exception.   
// As a best practice, derive your exception   
// directly or indirectly from std::exception.   
class myException : public std::exception {   
};  
int main()  
{  
    HANDLE aThread[THREADCOUNT];  
    DWORD ThreadID;  
  
    // Create secondary threads.  
    for( int i=0; i < THREADCOUNT; i++ )  
    {  
        aArg[i] = i;  
        aThread[i] = CreateThread(   
            NULL,       // Default security attributes.  
            0,          // Default stack size.  
            (LPTHREAD_START_ROUTINE) ThrowExceptions,   
            (LPVOID) &aArg[i], // Thread function argument.  
            0,          // Default creation flags.  
            &ThreadID); // Receives thread identifier.  
        if( aThread[i] == NULL )  
        {  
            printf("CreateThread error: %d\n", GetLastError());  
            return -1;  
        }  
    }   
  
    // Wait for all threads to terminate.  
    WaitForMultipleObjects(THREADCOUNT, aThread, TRUE, INFINITE);   
    // Close thread handles.  
    for( int i=0; i < THREADCOUNT; i++ ) {  
        CloseHandle(aThread[i]);   
    }  
  
    // Rethrow and catch the transported exceptions.  
    for ( int i = 0; i < THREADCOUNT; i++ ) {  
        try {  
            if (aException[i] == NULL) {  
                printf("exception_ptr %d: No exception was transported.\n", i);  
            }  
            else {  
                rethrow_exception( aException[i] );  
            }    
        }  
        catch( const invalid_argument & ) {  
            printf("exception_ptr %d: Caught an invalid_argument exception.\n", i);  
        }  
        catch( const myException & ) {  
            printf("exception_ptr %d: Caught a  myException exception.\n", i);  
        }  
    }  
}   
// Each thread throws an exception depending on its thread   
// function argument, and then ends.   
DWORD WINAPI ThrowExceptions( LPVOID lpParam )   
{   
    int x = *((int*)lpParam);  
    if (x == 0) {  
        try {  
            // Standard C++ exception.  
            // This example explicitly throws invalid_argument exception.   
            // In practice, your application performs an operation that   
            // implicitly throws an exception.  
            throw invalid_argument("A C++ exception.");  
        }    
        catch ( const invalid_argument & ) {   
            aException[x] = current_exception();  
        }   
    }  
    else {  
        // User-defined exception.  
        aException[x] = make_exception_ptr( myException() );   
    }  
    return TRUE;   
}  
```  
  
```Output  
exception_ptr 0: Caught an invalid_argument exception.  
exception_ptr 1: Caught a  myException exception.  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<wyjątku >  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)     
 [/EH (Model obsługi wyjątku)](../build/reference/eh-exception-handling-model.md)   
 [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md)
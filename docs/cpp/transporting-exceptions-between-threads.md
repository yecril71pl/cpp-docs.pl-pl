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
ms.openlocfilehash: 38c76d582a6bd30c5fa3f9285bc96853f7e9d162
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199482"
---
# <a name="transporting-exceptions-between-threads"></a>Transport wyjątków między wątkami

Visual C++ obsługuje *transportowanie wyjątków* z jednego wątku do innego. Transport wyjątków umożliwia przechwytywanie wyjątków w jednym wątku, a następnie powodowanie, aby były generowane w innym wątku. Na przykład, możesz użyć tej funkcji do pisania aplikacji wielowątkowych, gdzie wątek główny obsługuje wszystkie wyjątki generowane przez pomocnicze wątki. Transport wyjątków jest przydatny głównie dla deweloperów, którzy tworzą biblioteki lub systemy programowania równoległego. Aby zaimplementować transport wyjątków, Visual C++ zapewnia [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) typu i [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception), i [make_ exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) funkcji.

## <a name="syntax"></a>Składnia

```cpp
namespace std
{
   typedef unspecified exception_ptr;
   exception_ptr current_exception();
   void rethrow_exception(exception_ptr p);
   template<class E>
       exception_ptr make_exception_ptr(E e) noexcept;
}
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Nie określono tego parametru*|Nieokreślona Klasa wewnętrzna, która jest używana do zaimplementowania `exception_ptr` typu.|
|*p*|`exception_ptr` Obiekt, który odwołuje się do wyjątku.|
|*E*|Klasa, która reprezentuje wyjątek.|
|*e*|Wystąpienie parametru `E` klasy.|

## <a name="return-value"></a>Wartość zwracana

`current_exception` Funkcja zwraca `exception_ptr` obiekt, który odwołuje się do wyjątku, który jest obecnie w toku. Jeśli wyjątek nie jest w toku, funkcja zwraca `exception_ptr` obiektu, który nie jest skojarzony z żadnym wyjątkiem.

`make_exception_ptr` Funkcja zwraca `exception_ptr` obiektu, który odwołuje się do wyjątków określonych przez *e* parametru.

## <a name="remarks"></a>Uwagi

### <a name="scenario"></a>Scenariusz

Wyobraź sobie, że chcesz utworzyć aplikację, która może być skalowana, aby obsłużyć zmienną ilość pracy. Aby osiągnąć ten cel, projektujesz aplikację wielowątkową, gdzie wstępny, podstawowy wątek tworzy tyle wątków pomocniczych, ile potrzebuje, aby wykonać zadanie. Pomocnicze wątki pomagają wątkowi głównemu zarządzać zasobami, równoważyć obciążenia, a także zwiększać wydajność. Dzięki rozłożeniu pracy, aplikacja wielowątkowa działa lepiej niż aplikacja jednowątkowa.

Jednak jeśli wątek pomocniczy zgłasza wyjątek, wskazane jest, aby watek główny go obsłużył. To dlatego, że chcesz, aby aplikacja obsługiwała wyjątki w sposób spójny, jednolity, bez względu na liczbę wątków pomocniczych.

### <a name="solution"></a>Rozwiązanie

Aby obsłużyć poprzedni scenariusz, standard C++ obsługuje transportowanie wyjątków pomiędzy wątkami. Jeśli wątek pomocniczy zgłasza wyjątek, wyjątek ten staje się *bieżący wyjątek*. Poprzez analogię do świata rzeczywistego, bieżący wyjątek jest nazywany *w locie*. Bieżący wyjątek jest w locie od czasu, kiedy jest generowany, aż do momentu, gdy zostanie zwrócony przez kod obsługi wyjątków, który go przechwycił.

Wątek pomocniczy może przechwycić wyjątek bieżący w **catch** zablokować, a następnie wywołaj `current_exception` funkcji do przechowywania wyjątku w `exception_ptr` obiektu. `exception_ptr` Obiekt musi być dostępny dla pomocniczego wątku i wątku głównego. Na przykład `exception_ptr` obiekt może być zmienną globalną, do których dostęp jest kontrolowany przez mutex. Termin *transportować wyjątek* oznacza, że wyjątek w jednym wątku można przekonwertować na formularz, który może zostać oceniony przez inny wątek.

Następnie wątek główny wywołuje `rethrow_exception` funkcji, która wyodrębnia i następnie zgłasza wyjątek z `exception_ptr` obiektu. Wygenerowany wyjątek staje się bieżącym wyjątkiem w wątku głównym. Oznacza to, że wyjątek wygląda tak, jakby pochodził z wątku głównego.

Wreszcie, wątek główny może przechwycić wyjątek bieżący w **catch** zablokować, a następnie go przetworzyć lub zgłosić do wyższego poziomu obsługi wyjątków. Lub wątek główny może zignorować wyjątek i pozwolić zakończyć proces.

Większość aplikacji nie musi transportować wyjątków między wątkami. Jednak ta funkcja jest przydatna w systemach przetwarzania równoległego, ponieważ system może podzielić pracę pomiędzy wątki pomocnicze, procesory lub rdzenie. W środowisku przetwarzania równoległego pojedynczy, wyspecjalizowany wątek może obsługiwać wszystkie wyjątki z pomocniczych wątków i może stanowić spójny model obsługi wyjątków dla innych aplikacji.

Aby uzyskać więcej informacji o propozycji komitetu standardów C++, znajdź w Internecie dokument o numerze N2179 pod tytułem „Language Support for Transporting Exceptions between Threads” (Obsługa języka dla transportu wyjątków między wątkami).

### <a name="exception-handling-models-and-compiler-options"></a>Opcje kompilatora i modele obsługi wyjątków

Model obsługi wyjątków aplikacji określa, czy można przechwycić i transportować wyjątek. Visual C++ obsługuje trzy modele, które mogą obsługiwać wyjątki C++, obsługę wyjątków strukturalnych (SEH) i wyjątki środowiska uruchomieniowego języka wspólnego (CLR). Użyj [/EH](../build/reference/eh-exception-handling-model.md) i [/CLR](../build/reference/clr-common-language-runtime-compilation.md) opcji kompilatora, aby określić model obsługi wyjątków w aplikacji.

Tylko następujące połączenie opcji kompilatora i instrukcji programowania może transportować wyjątek. Inne połączenia nie mogą przechwytywać wyjątków lub mogą je przechwytywać, ale nie transportować.

- **/Eha** — opcja kompilatora i **catch** instrukcji transportuje wyjątki SEH i C++.

- **/Eha**, **/EHS**, i **/ehsc** opcje kompilatora i **catch** poufności informacji mogą transportować wyjątki C++.

- **/CLR** — opcja kompilatora i **catch** poufności informacji mogą transportować wyjątki C++. **/CLR** — opcja kompilatora oznacza określenie **/eha** opcji. Należy zauważyć, że kompilator nie obsługuje transportowania wyjątków zarządzanych. Jest to spowodowane wyjątki zarządzane, które są uzyskiwane z [klasy System.Exception](../standard-library/exception-class.md), są już obiektami, które mogą być przenoszone między wątkami przy użyciu środowiska uruchomieniowego wspólnego wyprowadzane.

   > [!IMPORTANT]
   > Firma Microsoft zaleca, aby określić **/ehsc** — opcja kompilatora i przechwytywać tylko wyjątki C++. Można się narazić na zagrożenia bezpieczeństwa, jeśli używasz **/eha** lub **/CLR** — opcja kompilatora i **catch** instrukcji z wielokropkiem  *deklaracji wyjątku* (`catch(...)`). Zamierzasz prawdopodobnie używać **catch** instrukcję, aby przechwycić kilka szczególnych wyjątków. Jednak `catch(...)` instrukcji przechwytuje wyjątki wszystkich języków C++ i SEH, w tym nieoczekiwane, które powinny być krytyczne. Jeśli zignorujesz lub źle obsłużysz nieoczekiwany wyjątek, złośliwy kod wykorzystać tę szansę do obejścia zabezpieczeń programu.

## <a name="usage"></a>Użycie

W poniższych sekcjach opisano sposób transportu wyjątków za pomocą `exception_ptr` typu i `current_exception`, `rethrow_exception`, i `make_exception_ptr` funkcji.

## <a name="exceptionptr-type"></a>Typ exception_ptr

Użyj `exception_ptr` obiekt, aby odwoływać się do bieżącego wyjątku lub wystąpienia wyjątku określonego przez użytkownika. W implementacji firmy Microsoft wyjątek jest reprezentowany przez [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-_exception_record) struktury. Każdy `exception_ptr` obiekt zawiera pole odwołania wyjątku wskazuje kopię `EXCEPTION_RECORD` strukturę, która reprezentuje wyjątek.

Kiedy Deklarujesz `exception_ptr` zmiennej, zmienna nie jest skojarzony z żadnym wyjątkiem. To znaczy, że pole odwołania wyjątku ma wartość NULL. Takie `exception_ptr` obiekt jest nazywany *null exception_ptr*.

Użyj `current_exception` lub `make_exception_ptr` funkcję, aby przypisać wyjątek do `exception_ptr` obiektu. Podczas przypisywania wyjątku do `exception_ptr` zmiennej, pole odwołania wyjątku zmiennej wskazuje kopię wyjątku. W przypadku braku pamięci, aby skopiować wyjątek, pole odwołania wyjątku wskazuje kopię [std::bad_alloc](../standard-library/bad-alloc-class.md) wyjątku. Jeśli `current_exception` lub `make_exception_ptr` funkcji nie może skopiować wyjątku jakiegokolwiek innego powodu, wywołania funkcji [zakończyć](../c-runtime-library/reference/terminate-crt.md) funkcję, aby zakończyć bieżący proces.

Pomimo swojej nazwy `exception_ptr` obiektu sam nie jest wskaźnikiem. Go nie stosuje semantyki wskaźnika i nie można używać z dostępu do elementu członkowskiego wskaźnika (`->`) lub pośrednio (`*`) operatorów. `exception_ptr` Obiekt nie ma publicznych elementów członkowskich danych ani funkcji elementów członkowskich.

### <a name="comparisons"></a>Porównania

Możesz użyć równości (`==`) i nierówności (`!=`) operatory do porównywania dwóch `exception_ptr` obiektów. Operatory nie porównują wartość binarna (wzorca bitowego) `EXCEPTION_RECORD` struktur, które reprezentują wyjątki. Zamiast tego, operatory porównują adresy w polu odwołania do wyjątku `exception_ptr` obiektów. W związku z tym, o wartości null `exception_ptr` i porównywane równe wartości NULL.

## <a name="currentexception-function"></a>Funkcja current_exception

Wywołaj `current_exception` działa w programach **catch** bloku. Jeśli wyjątek jest w locie i **catch** bloku może przechwycić wyjątek, `current_exception` funkcja zwraca `exception_ptr` obiekt, który odwołuje się do wyjątku. W przeciwnym razie funkcja zwraca wartość null `exception_ptr` obiektu.

### <a name="details"></a>Szczegóły

`current_exception` Funkcja przechwytuje wyjątek, który jest w locie, niezależnie od tego, czy **catch** instrukcja Określa [deklaracji wyjątku](../cpp/try-throw-and-catch-statements-cpp.md) instrukcji.

Destruktor dla bieżącego wyjątku jest wywoływany pod koniec **catch** zablokować, jeśli nie jest ponownie zgłaszany wyjątek. Jednak nawet wtedy, gdy wywołujesz `current_exception` funkcji w destruktorze, funkcja zwraca `exception_ptr` obiektu, który odwołuje się do bieżącego wyjątku.

Kolejne wywołania `current_exception` funkcji powrotu `exception_ptr` obiekty, które odwołują się do różnych kopii bieżącego wyjątku. W związku z tym obiekty są porównane jako nierówne, ponieważ odnoszą się one do poszczególnych kopii, mimo że kopie mają tę samą wartość binarną.

### <a name="seh-exceptions"></a>Wyjątki SEH

Jeśli używasz **/eha** opcję kompilatora przechwytujesz wyjątek SEH w języku C++ **catch** bloku. `current_exception` Funkcja zwraca `exception_ptr` obiekt, który odwołuje się do wyjątku SEH. I `rethrow_exception` funkcja zgłasza wyjątek SEH, jeśli wywołujesz ją z thetransported `exception_ptr` obiekt jako argumentu.

`current_exception` Funkcja zwraca wartość null `exception_ptr` Jeśli wywołasz ją w SEH **__finally** obsługi zakończenia **__except** obsługi wyjątków lub **__except**wyrażenie filtru.

Transportowany wyjątek nie obsługuje wyjątków zagnieżdżonych. Wyjątek zagnieżdżony występuje, jeśli podczas obsługi wyjątku jest zgłaszany inny wyjątek. Jeśli przechwytujesz wyjątek zagnieżdżony `EXCEPTION_RECORD.ExceptionRecord` element członkowski danych wskazuje łańcuch `EXCEPTION_RECORD` struktur, które opisują wyjątki skojarzone. `current_exception` Funkcja nie obsługuje wyjątków zagnieżdżonych, ponieważ zwraca `exception_ptr` którego `ExceptionRecord` element członkowski danych jest zerowany.

Jeśli przechwytujesz wyjątek SEH, musisz zarządzać pamięcią, do przywoływane przez dowolny wskaźnik w `EXCEPTION_RECORD.ExceptionInformation` tablicy elementów członkowskich danych. Musisz gwarantować, że pamięć jest prawidłowa w okresie istnienia odpowiadającego `exception_ptr` obiektu i że pamięć jest zwalniana podczas `exception_ptr` obiekt zostanie usunięty.

Można użyć funkcji tłumacza wyjątków strukturalnych (SE) wraz z funkcją transportu wyjątków. Jeśli wyjątek SEH jest tłumaczony na wyjątek C++ `current_exception` funkcja zwraca `exception_ptr` odwołujący się do przetłumaczonego wyjątku zamiast oryginalnego wyjątku SEH. `rethrow_exception` Funkcja generuje następnie przetłumaczony wyjątek, a nie wyjątek oryginalny. Aby uzyskać więcej informacji o funkcjach tłumacza SE, zobacz [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="rethrowexception-function"></a>Funkcja rethrow_exception

Po zapisaniu przechwyconego wyjątku w `exception_ptr` obiektu, wątek główny może przetworzyć obiekt. W podstawowym wątku, wywołaj `rethrow_exception` działać razem z `exception_ptr` obiekt jako argumentu. `rethrow_exception` Funkcja wyodrębnia wyjątek z `exception_ptr` obiektu i następnie zgłasza wyjątek w kontekście wątku głównego. Jeśli *p* parametru `rethrow_exception` funkcji ma wartość null `exception_ptr`, funkcja zgłasza [std::bad_exception](../standard-library/bad-exception-class.md).

Wyodrębniony wyjątek jest teraz wyjątkiem bieżącym w wątku podstawowym i można go obsłużyć, podobnie jak w przypadku innych wyjątków. Jeśli przechwytujesz wyjątek, możesz go obsługiwać bezpośrednio lub użyć **throw** instrukcję, aby wysłać go do wyższego poziomu obsługi wyjątków. W przeciwnym razie nic nie rób, niech domyślny program obsługi wyjątków systemu zakończy proces.

## <a name="makeexceptionptr-function"></a>Funkcja make_exception_ptr

`make_exception_ptr` Funkcja przyjmuje instancję klasy jako argument, a następnie zwraca `exception_ptr` która odwołuje się do wystąpienia. Zwykle określaj [klasy wyjątku](../standard-library/exception-class.md) obiekt jako argument `make_exception_ptr` funkcji, mimo że dowolny obiekt klasy może być argumentem.

Wywoływanie `make_exception_ptr` funkcji jest odpowiednikiem zgłaszania wyjątku C++, przechwytywania go w **catch** bloku, a następnie wywoływania `current_exception` funkcja zwraca `exception_ptr` obiekt, który odwołuje się do wyjątku. Implementacja firmy Microsoft `make_exception_ptr` jest bardziej efektywna niż generowanie i następnie przechwytywanie wyjątku.

Aplikacja zazwyczaj nie wymaga `make_exception_ptr` funkcji, a my odradzamy jej użycie.

## <a name="example"></a>Przykład

Poniższy przykład transportuje standardowy wyjątek C++ i niestandardowy wyjątek C++ z jednego wątku do innego.

```cpp
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

## <a name="see-also"></a>Zobacz także
 [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)  
 [/EH (Model obsługi wyjątku)](../build/reference/eh-exception-handling-model.md)  
 [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md)
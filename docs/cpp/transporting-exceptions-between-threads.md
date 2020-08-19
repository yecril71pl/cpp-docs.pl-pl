---
title: Transport wyjątków między wątkami
ms.date: 05/07/2019
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
ms.openlocfilehash: c3ba61062421462dea8f4280575be9f00ac3931a
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561365"
---
# <a name="transporting-exceptions-between-threads"></a>Transport wyjątków między wątkami

Kompilator języka Microsoft C++ (MSVC) obsługuje *transportowanie wyjątku* z jednego wątku do innego. Transport wyjątków umożliwia przechwytywanie wyjątków w jednym wątku, a następnie powodowanie, aby były generowane w innym wątku. Na przykład, możesz użyć tej funkcji do pisania aplikacji wielowątkowych, gdzie wątek główny obsługuje wszystkie wyjątki generowane przez pomocnicze wątki. Transport wyjątków jest przydatny głównie dla deweloperów, którzy tworzą biblioteki lub systemy programowania równoległego. Aby zaimplementować transportowanie wyjątków, MSVC udostępnia typ [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) oraz funkcje [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)i [make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) .

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

*nieokreślony*\
Nieokreślona Klasa wewnętrzna, która jest używana do implementowania `exception_ptr` typu.

*St*\
`exception_ptr`Obiekt, który odwołuje się do wyjątku.

*Adres*\
Klasa, która reprezentuje wyjątek.

*adres*\
Wystąpienie `E` klasy Parameter.

## <a name="return-value"></a>Wartość zwracana

`current_exception`Funkcja zwraca `exception_ptr` obiekt, który odwołuje się do wyjątku, który jest aktualnie w toku. Jeśli żaden wyjątek nie jest w toku, funkcja zwraca `exception_ptr` obiekt, który nie jest skojarzony z żadnym wyjątkiem.

`make_exception_ptr`Funkcja zwraca `exception_ptr` obiekt, który odwołuje się do wyjątku określonego przez parametr *e* .

## <a name="remarks"></a>Uwagi

### <a name="scenario"></a>Scenariusz

Wyobraź sobie, że chcesz utworzyć aplikację, która może być skalowana, aby obsłużyć zmienną ilość pracy. Aby osiągnąć ten cel, projektujesz aplikację wielowątkową, gdzie wstępny, podstawowy wątek tworzy tyle wątków pomocniczych, ile potrzebuje, aby wykonać zadanie. Pomocnicze wątki pomagają wątkowi głównemu zarządzać zasobami, równoważyć obciążenia, a także zwiększać wydajność. Dzięki rozłożeniu pracy, aplikacja wielowątkowa działa lepiej niż aplikacja jednowątkowa.

Jednak jeśli wątek pomocniczy zgłasza wyjątek, wskazane jest, aby watek główny go obsłużył. To dlatego, że chcesz, aby aplikacja obsługiwała wyjątki w sposób spójny, jednolity, bez względu na liczbę wątków pomocniczych.

### <a name="solution"></a>Rozwiązanie

Aby obsłużyć poprzedni scenariusz, standard C++ obsługuje transportowanie wyjątków pomiędzy wątkami. Jeśli wątek pomocniczy zgłasza wyjątek, ten wyjątek zmieni się na *bieżący wyjątek*. Analogicznie do rzeczywistego świata, bieżący wyjątek jest uznawany za *w locie*. Bieżący wyjątek jest w locie od czasu, kiedy jest generowany, aż do momentu, gdy zostanie zwrócony przez kod obsługi wyjątków, który go przechwycił.

Wątek pomocniczy może przechwycić bieżący wyjątek w **`catch`** bloku, a następnie wywołać funkcję w `current_exception` celu zapisania wyjątku w `exception_ptr` obiekcie. `exception_ptr`Obiekt musi być dostępny dla wątku pomocniczego i do wątku głównego. Na przykład `exception_ptr` obiekt może być zmienną globalną, której dostęp jest kontrolowany przez mutex. Termin *transport wyjątku* oznacza, że wyjątek w jednym wątku można przekonwertować na formularz, do którego można uzyskać dostęp za pomocą innego wątku.

Następnie wątek podstawowy wywołuje `rethrow_exception` funkcję, która wyodrębnia, a następnie zgłasza wyjątek z `exception_ptr` obiektu. Wygenerowany wyjątek staje się bieżącym wyjątkiem w wątku głównym. Oznacza to, że wyjątek wygląda tak, jakby pochodził z wątku głównego.

Na koniec wątek główny może przechwycić bieżący wyjątek w **`catch`** bloku, a następnie przetworzyć go lub zgłosić do programu obsługi wyjątków wyższego poziomu. Lub wątek główny może zignorować wyjątek i pozwolić zakończyć proces.

Większość aplikacji nie musi transportować wyjątków między wątkami. Jednak ta funkcja jest przydatna w systemach przetwarzania równoległego, ponieważ system może podzielić pracę pomiędzy wątki pomocnicze, procesory lub rdzenie. W środowisku przetwarzania równoległego pojedynczy, wyspecjalizowany wątek może obsługiwać wszystkie wyjątki z pomocniczych wątków i może stanowić spójny model obsługi wyjątków dla innych aplikacji.

Aby uzyskać więcej informacji o propozycji komitetu standardów C++, znajdź w Internecie dokument o numerze N2179 pod tytułem „Language Support for Transporting Exceptions between Threads” (Obsługa języka dla transportu wyjątków między wątkami).

### <a name="exception-handling-models-and-compiler-options"></a>Modele obsługi wyjątków i opcje kompilatora

Model obsługi wyjątków aplikacji określa, czy można przechwycić i transportować wyjątek. Visual C++ obsługuje trzy modele, które mogą obsługiwać wyjątki C++, obsługę wyjątków strukturalnych (SEH) i wyjątki środowiska uruchomieniowego języka wspólnego (CLR). Użyj opcji kompilatora [/EH](../build/reference/eh-exception-handling-model.md) i [/CLR](../build/reference/clr-common-language-runtime-compilation.md) , aby określić model obsługi wyjątków aplikacji.

Tylko następujące połączenie opcji kompilatora i instrukcji programowania może transportować wyjątek. Inne połączenia nie mogą przechwytywać wyjątków lub mogą je przechwytywać, ale nie transportować.

- Opcja kompilatora **/EHa** i **`catch`** instrukcja może transportować wyjątki SEH i C++.

- Opcje kompilatora **/EHa**, **/EHS**i **/EHsc** , a **`catch`** instrukcja mogą transportować wyjątki C++.

- Opcja kompilatora **/CLR** i **`catch`** instrukcja może transportować wyjątki C++. Opcja kompilatora **/CLR** implikuje specyfikację opcji **/EHa** . Należy zauważyć, że kompilator nie obsługuje transportowania wyjątków zarządzanych. Wynika to z faktu, że zarządzane wyjątki, które pochodzą z [klasy System. Exception](../standard-library/exception-class.md), są już obiektami, które można przenosić między wątkami przy użyciu obiektów wspólnego środowiska uruchomieniowego języka.

   > [!IMPORTANT]
   > Zalecamy określenie opcji kompilatora **/EHsc** i przechwycenie tylko wyjątków C++. Jeśli używasz opcji kompilatora **/EHa** lub **/CLR** i **`catch`** instrukcji z *deklaracją wyjątku* wielokropka (), narażasz się na zagrożenia bezpieczeństwa `catch(...)` . Prawdopodobnie zamierzasz użyć **`catch`** instrukcji w celu przechwycenia kilku określonych wyjątków. Jednak `catch(...)` instrukcja przechwytuje wszystkie wyjątki C++ i SEH, w tym nieoczekiwane, które powinny być krytyczne. Jeśli zignorujesz lub źle obsłużysz nieoczekiwany wyjątek, złośliwy kod wykorzystać tę szansę do obejścia zabezpieczeń programu.

## <a name="usage"></a>Użycie

W poniższych sekcjach opisano, jak transportować wyjątki przy użyciu `exception_ptr` typu, `current_exception` oraz `rethrow_exception` funkcji, i `make_exception_ptr` .

## <a name="exception_ptr-type"></a>Typ exception_ptr

Użyj `exception_ptr` obiektu, aby odwołać się do bieżącego wyjątku lub wystąpienia wyjątku określonego przez użytkownika. W implementacji firmy Microsoft wyjątek jest reprezentowany przez strukturę [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) . Każdy `exception_ptr` obiekt zawiera pole odwołania wyjątku, które wskazuje kopię `EXCEPTION_RECORD` struktury, która reprezentuje wyjątek.

Podczas deklarowania `exception_ptr` zmiennej zmienna nie jest skojarzona z żadnym wyjątkiem. To znaczy, że pole odwołania wyjątku ma wartość NULL. Taki `exception_ptr` obiekt jest nazywany exception_ptr o *wartości null*.

Użyj `current_exception` funkcji or, `make_exception_ptr` Aby przypisać wyjątek do `exception_ptr` obiektu. Po przypisaniu wyjątku do `exception_ptr` zmiennej pole odwołania wyjątku zmiennej wskazuje kopię wyjątku. Jeśli nie ma wystarczającej ilości pamięci do skopiowania wyjątku, pole odwołania wyjątku wskazuje kopię wyjątku [std:: bad_alloc](../standard-library/bad-alloc-class.md) . Jeśli `current_exception` Funkcja or `make_exception_ptr` nie może skopiować wyjątku z innych przyczyn, funkcja wywołuje funkcję [Terminate](../c-runtime-library/reference/terminate-crt.md) , aby wyjść z bieżącego procesu.

Pomimo nazwy, `exception_ptr` obiekt nie jest samo wskaźnikiem. Nie przestrzega on semantyki wskaźnika i nie można go używać z operatorami dostępu do elementów członkowskich wskaźnika ( `->` ) ani pośrednimi ( `*` ). `exception_ptr`Obiekt nie ma publicznych składowych danych ani funkcji Członkowskich.

### <a name="comparisons"></a>Porównania

`==` `!=` Do porównywania dwóch obiektów można użyć operatorów równości () i nierówności () `exception_ptr` . Operatory nie porównują wartości binarnej (wzorca bitowego) `EXCEPTION_RECORD` struktur, które reprezentują wyjątki. Zamiast tego operatory porównują adresy w polu odwołanie wyjątku `exception_ptr` obiektów. W związku z tym `exception_ptr` wartość null i wartości null są porównywane jako równe.

## <a name="current_exception-function"></a>Funkcja current_exception

Wywołaj `current_exception` funkcję w **`catch`** bloku. Jeśli wyjątek jest w locie i **`catch`** blok może przechwycić wyjątek, `current_exception` Funkcja zwraca `exception_ptr` obiekt, który odwołuje się do wyjątku. W przeciwnym razie funkcja zwraca obiekt o wartości null `exception_ptr` .

### <a name="details"></a>Szczegóły

`current_exception`Funkcja przechwytuje wyjątek, który jest w locie, niezależnie od tego, czy **`catch`** instrukcja określa instrukcję [deklaracji wyjątku](../cpp/try-throw-and-catch-statements-cpp.md) .

Destruktor dla bieżącego wyjątku jest wywoływany na końcu **`catch`** bloku, jeśli nie zostanie ponownie zgłoszony wyjątek. Jednak nawet w przypadku wywołania `current_exception` funkcji w destruktorze funkcja zwraca `exception_ptr` obiekt, który odwołuje się do bieżącego wyjątku.

Kolejne wywołania `current_exception` funkcji zwracają `exception_ptr` obiekty odwołujące się do różnych kopii bieżącego wyjątku. W związku z tym obiekty są porównane jako nierówne, ponieważ odnoszą się one do poszczególnych kopii, mimo że kopie mają tę samą wartość binarną.

### <a name="seh-exceptions"></a>Wyjątki SEH

Jeśli używasz opcji kompilatora **/EHa** , możesz przechwycić wyjątek SEH w **`catch`** bloku C++. `current_exception`Funkcja zwraca `exception_ptr` obiekt, który odwołuje się do wyjątku SEH. `rethrow_exception`Funkcja zgłasza wyjątek SEH, jeśli jest wywoływana z `exception_ptr` obiektem thetransported jako argumentem.

`current_exception`Funkcja zwraca wartość null `exception_ptr` , jeśli wywołuje ją w **`__finally`** procedurze obsługi zakończenia SEH, **`__except`** obsłudze wyjątku lub **`__except`** wyrażeniu filtru.

Transportowany wyjątek nie obsługuje wyjątków zagnieżdżonych. Wyjątek zagnieżdżony występuje, jeśli podczas obsługi wyjątku jest zgłaszany inny wyjątek. Jeśli przechwytywany jest wyjątek zagnieżdżony, `EXCEPTION_RECORD.ExceptionRecord` element członkowski danych wskazuje łańcuch `EXCEPTION_RECORD` struktur, które opisują skojarzone wyjątki. `current_exception`Funkcja nie obsługuje zagnieżdżonych wyjątków, ponieważ zwraca obiekt, `exception_ptr` którego `ExceptionRecord` składowa danych jest różna od zera.

W przypadku przechwycenia wyjątku SEH należy zarządzać pamięcią, do której odwołuje się dowolny wskaźnik w `EXCEPTION_RECORD.ExceptionInformation` tablicy elementów członkowskich danych. Należy zagwarantować, że pamięć jest prawidłowa w okresie istnienia odpowiedniego `exception_ptr` obiektu i że pamięć jest zwalniana po `exception_ptr` usunięciu obiektu.

Można użyć funkcji tłumacza wyjątków strukturalnych (SE) wraz z funkcją transportu wyjątków. Jeśli wyjątek SEH jest tłumaczony na wyjątek języka C++, `current_exception` Funkcja zwraca `exception_ptr` odwołujący się do przetłumaczonego wyjątku zamiast oryginalnego wyjątku SEH. `rethrow_exception`Następnie funkcja zgłasza wyjątek przetłumaczony, a nie oryginalny wyjątek. Aby uzyskać więcej informacji dotyczących funkcji usługi translator, zobacz [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="rethrow_exception-function"></a>Funkcja rethrow_exception

Po przechowaniu przechwyconego wyjątku w `exception_ptr` obiekcie wątek główny może przetworzyć obiekt. W wątku podstawowym Wywołaj `rethrow_exception` funkcję razem z `exception_ptr` obiektem jako argumentem. `rethrow_exception`Funkcja wyodrębnia wyjątek z `exception_ptr` obiektu, a następnie zgłasza wyjątek w kontekście wątku głównego. Jeśli parametr *p* `rethrow_exception` funkcji ma wartość null `exception_ptr` , funkcja zgłasza [std:: bad_exception](../standard-library/bad-exception-class.md).

Wyodrębniony wyjątek jest teraz wyjątkiem bieżącym w wątku podstawowym i można go obsłużyć, podobnie jak w przypadku innych wyjątków. W przypadku przechwycenia wyjątku można go obsłużyć natychmiast lub użyć **`throw`** instrukcji, aby wysłać ją do programu obsługi wyjątków wyższego poziomu. W przeciwnym razie nic nie rób, niech domyślny program obsługi wyjątków systemu zakończy proces.

## <a name="make_exception_ptr-function"></a>make_exception_ptr, funkcja

`make_exception_ptr`Funkcja przyjmuje wystąpienie klasy jako argument, a następnie zwraca `exception_ptr` odwołanie odwołujące się do wystąpienia. Zazwyczaj należy określić obiekt [klasy wyjątku](../standard-library/exception-class.md) jako argument `make_exception_ptr` funkcji, chociaż każdy obiekt klasy może być argumentem.

Wywołanie `make_exception_ptr` funkcji jest równoznaczne z wygenerowaniem wyjątku C++, przechwyceniem go w **`catch`** bloku, a następnie wywołaniem `current_exception` funkcji zwracającej `exception_ptr` obiekt, który odwołuje się do wyjątku. Implementacja firmy Microsoft dla `make_exception_ptr` funkcji jest bardziej wydajna niż zgłaszanie i przechwytywanie wyjątku.

Aplikacja zwykle nie wymaga `make_exception_ptr` funkcji i odradza jej używanie.

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

**Nagłówek:**\<exception>

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)<br/>
[/EH (model obsługi wyjątków)](../build/reference/eh-exception-handling-model.md)<br/>
[/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md)

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
ms.openlocfilehash: ca6ad9f9b923843d74a3b671691438af6ea5d82b
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68917026"
---
# <a name="transporting-exceptions-between-threads"></a>Transport wyjątków między wątkami

Kompilator firmy C++ Microsoft (MSVC) obsługuje *transportowanie wyjątku* z jednego wątku do innego. Transport wyjątków umożliwia przechwytywanie wyjątków w jednym wątku, a następnie powodowanie, aby były generowane w innym wątku. Na przykład, możesz użyć tej funkcji do pisania aplikacji wielowątkowych, gdzie wątek główny obsługuje wszystkie wyjątki generowane przez pomocnicze wątki. Transport wyjątków jest przydatny głównie dla deweloperów, którzy tworzą biblioteki lub systemy programowania równoległego. Aby zaimplementować transportowanie wyjątków, MSVC udostępnia typ [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) oraz funkcje [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)i [make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) .

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
|*nieokreślony*|Nieokreślona Klasa wewnętrzna, która jest używana do implementowania `exception_ptr` typu.|
|*p*|`exception_ptr` Obiekt, który odwołuje się do wyjątku.|
|*E*|Klasa, która reprezentuje wyjątek.|
|*e*|Wystąpienie klasy Parameter `E` .|

## <a name="return-value"></a>Wartość zwracana

`current_exception` Funkcja`exception_ptr` zwraca obiekt, który odwołuje się do wyjątku, który jest aktualnie w toku. Jeśli żaden wyjątek nie jest w toku, funkcja zwraca `exception_ptr` obiekt, który nie jest skojarzony z żadnym wyjątkiem.

Funkcja zwraca obiekt, który odwołuje się do wyjątku określonego przez parametr *e.* `make_exception_ptr` `exception_ptr`

## <a name="remarks"></a>Uwagi

### <a name="scenario"></a>Scenariusz

Wyobraź sobie, że chcesz utworzyć aplikację, która może być skalowana, aby obsłużyć zmienną ilość pracy. Aby osiągnąć ten cel, projektujesz aplikację wielowątkową, gdzie wstępny, podstawowy wątek tworzy tyle wątków pomocniczych, ile potrzebuje, aby wykonać zadanie. Pomocnicze wątki pomagają wątkowi głównemu zarządzać zasobami, równoważyć obciążenia, a także zwiększać wydajność. Dzięki rozłożeniu pracy, aplikacja wielowątkowa działa lepiej niż aplikacja jednowątkowa.

Jednak jeśli wątek pomocniczy zgłasza wyjątek, wskazane jest, aby watek główny go obsłużył. To dlatego, że chcesz, aby aplikacja obsługiwała wyjątki w sposób spójny, jednolity, bez względu na liczbę wątków pomocniczych.

### <a name="solution"></a>Rozwiązanie

Aby obsłużyć poprzedni scenariusz, standard C++ obsługuje transportowanie wyjątków pomiędzy wątkami. Jeśli wątek pomocniczy zgłasza wyjątek, ten wyjątek zmieni się na *bieżący wyjątek*. Analogicznie do rzeczywistego świata, bieżący wyjątek jest uznawany za *w locie*. Bieżący wyjątek jest w locie od czasu, kiedy jest generowany, aż do momentu, gdy zostanie zwrócony przez kod obsługi wyjątków, który go przechwycił.

Wątek pomocniczy może przechwycić bieżący wyjątek w bloku **catch** , a następnie wywołać `current_exception` funkcję w celu zapisania wyjątku w `exception_ptr` obiekcie. `exception_ptr` Obiekt musi być dostępny dla wątku pomocniczego i do wątku głównego. Na przykład `exception_ptr` obiekt może być zmienną globalną, której dostęp jest kontrolowany przez mutex. Termin *transport wyjątku* oznacza, że wyjątek w jednym wątku można przekonwertować na formularz, do którego można uzyskać dostęp za pomocą innego wątku.

Następnie wątek podstawowy wywołuje `rethrow_exception` funkcję, która wyodrębnia, a następnie zgłasza wyjątek `exception_ptr` z obiektu. Wygenerowany wyjątek staje się bieżącym wyjątkiem w wątku głównym. Oznacza to, że wyjątek wygląda tak, jakby pochodził z wątku głównego.

Na koniec wątek główny może przechwycić bieżący wyjątek w bloku **catch** , a następnie przetworzyć go lub zgłosić do programu obsługi wyjątków wyższego poziomu. Lub wątek główny może zignorować wyjątek i pozwolić zakończyć proces.

Większość aplikacji nie musi transportować wyjątków między wątkami. Jednak ta funkcja jest przydatna w systemach przetwarzania równoległego, ponieważ system może podzielić pracę pomiędzy wątki pomocnicze, procesory lub rdzenie. W środowisku przetwarzania równoległego pojedynczy, wyspecjalizowany wątek może obsługiwać wszystkie wyjątki z pomocniczych wątków i może stanowić spójny model obsługi wyjątków dla innych aplikacji.

Aby uzyskać więcej informacji o propozycji komitetu standardów C++, znajdź w Internecie dokument o numerze N2179 pod tytułem „Language Support for Transporting Exceptions between Threads” (Obsługa języka dla transportu wyjątków między wątkami).

### <a name="exception-handling-models-and-compiler-options"></a>Opcje kompilatora i modele obsługi wyjątków

Model obsługi wyjątków aplikacji określa, czy można przechwycić i transportować wyjątek. Visual C++ obsługuje trzy modele, które mogą obsługiwać wyjątki C++, obsługę wyjątków strukturalnych (SEH) i wyjątki środowiska uruchomieniowego języka wspólnego (CLR). Użyj opcji kompilatora [/EH](../build/reference/eh-exception-handling-model.md) i [/CLR](../build/reference/clr-common-language-runtime-compilation.md) , aby określić model obsługi wyjątków aplikacji.

Tylko następujące połączenie opcji kompilatora i instrukcji programowania może transportować wyjątek. Inne połączenia nie mogą przechwytywać wyjątków lub mogą je przechwytywać, ale nie transportować.

- Opcja kompilatora **/EHa** i instrukcja **catch** mogą transportować SEH i C++ wyjątki.

- Opcje kompilatora **/EHa**, **/EHS**i **/EHsc** oraz instrukcja **catch** mogą transportować C++ wyjątki.

- Opcja kompilatora **/CLR** i instrukcja **catch** mogą transportować C++ wyjątki. Opcja kompilatora **/CLR** implikuje specyfikację opcji **/EHa** . Należy zauważyć, że kompilator nie obsługuje transportowania wyjątków zarządzanych. Wynika to z faktu, że zarządzane wyjątki, które pochodzą z [klasy System. Exception](../standard-library/exception-class.md), są już obiektami, które można przenosić między wątkami przy użyciu obiektów wspólnego środowiska uruchomieniowego języka.

   > [!IMPORTANT]
   > Zalecamy określenie opcji kompilatora **/EHsc** i przechwycenie tylko C++ wyjątków. Jeśli używasz opcji kompilatora **/EHa** lub **/CLR** i instrukcji **catch** z *deklaracją wyjątku* wielokropka (`catch(...)`), narażasz się na zagrożenia bezpieczeństwa. Prawdopodobnie zamierzasz użyć instrukcji **catch** do przechwycenia kilku określonych wyjątków. Jednak instrukcja przechwytuje wszystkie i SEH wyjątki, w tym nieoczekiwane, które powinny być krytyczne. C++ `catch(...)` Jeśli zignorujesz lub źle obsłużysz nieoczekiwany wyjątek, złośliwy kod wykorzystać tę szansę do obejścia zabezpieczeń programu.

## <a name="usage"></a>Użycie

W poniższych sekcjach opisano, jak transportować wyjątki `exception_ptr` przy użyciu typu, `current_exception`oraz `rethrow_exception`funkcji, `make_exception_ptr` i.

## <a name="exception_ptr-type"></a>Typ exception_ptr

`exception_ptr` Użyj obiektu, aby odwołać się do bieżącego wyjątku lub wystąpienia wyjątku określonego przez użytkownika. W implementacji firmy Microsoft wyjątek jest reprezentowany przez strukturę [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-exception_record) . Każdy `exception_ptr` obiekt zawiera pole odwołania wyjątku, które wskazuje kopię `EXCEPTION_RECORD` struktury, która reprezentuje wyjątek.

Podczas deklarowania `exception_ptr` zmiennej zmienna nie jest skojarzona z żadnym wyjątkiem. To znaczy, że pole odwołania wyjątku ma wartość NULL. Taki obiekt jest nazywany exception_ptr o *wartości null.* `exception_ptr`

Użyj funkcji `make_exception_ptr` `exception_ptr` or, aby przypisać wyjątek do obiektu. `current_exception` Po przypisaniu wyjątku do `exception_ptr` zmiennej pole odwołania wyjątku zmiennej wskazuje kopię wyjątku. Jeśli nie ma wystarczającej ilości pamięci do skopiowania wyjątku, pole odwołania wyjątku wskazuje kopię wyjątku [std:: bad_alloc](../standard-library/bad-alloc-class.md) . Jeśli funkcja `make_exception_ptr` or nie może skopiować wyjątku z innych przyczyn, funkcja wywołuje funkcję Terminate, aby wyjść z bieżącego procesu. [](../c-runtime-library/reference/terminate-crt.md) `current_exception`

Pomimo nazwy, `exception_ptr` obiekt nie jest samo wskaźnikiem. Nie przestrzega on semantyki wskaźnika i nie można go używać z operatorami dostępu do elementów`->`członkowskich wskaźnika () ani pośrednimi (`*`). `exception_ptr` Obiekt nie ma publicznych składowych danych ani funkcji Członkowskich.

### <a name="comparisons"></a>Porównania

Do porównywania dwóch`==` `exception_ptr` obiektów można użyć operatorów równości () i`!=`nierówności (). Operatory nie porównują wartości binarnej (wzorca bitowego) `EXCEPTION_RECORD` struktur, które reprezentują wyjątki. Zamiast tego operatory porównują adresy w polu `exception_ptr` odwołanie wyjątku obiektów. W związku z tym wartość `exception_ptr` null i wartości null są porównywane jako równe.

## <a name="current_exception-function"></a>Funkcja current_exception

Wywołaj funkcję w bloku **catch.** `current_exception` Jeśli wyjątek jest w locie i blok **catch** może przechwycić wyjątek, `current_exception` funkcja zwraca `exception_ptr` obiekt, który odwołuje się do wyjątku. W przeciwnym razie funkcja zwraca obiekt o `exception_ptr` wartości null.

### <a name="details"></a>Szczegóły

Funkcja przechwytuje wyjątek, który jest w locie, niezależnie od tego, czy instrukcja **catch** określa deklarację [wyjątku.](../cpp/try-throw-and-catch-statements-cpp.md) `current_exception`

Destruktor dla bieżącego wyjątku jest wywoływany na końcu bloku **catch** , jeśli ten wyjątek nie zostanie ponownie zgłoszony. Jednak nawet w przypadku wywołania `current_exception` funkcji w destruktorze funkcja `exception_ptr` zwraca obiekt, który odwołuje się do bieżącego wyjątku.

Kolejne wywołania `current_exception` funkcji zwracają `exception_ptr` obiekty odwołujące się do różnych kopii bieżącego wyjątku. W związku z tym obiekty są porównane jako nierówne, ponieważ odnoszą się one do poszczególnych kopii, mimo że kopie mają tę samą wartość binarną.

### <a name="seh-exceptions"></a>Wyjątki SEH

Jeśli używasz opcji kompilatora **/EHa** , możesz przechwycić wyjątek SEH w C++ bloku **catch** . `current_exception` Funkcja`exception_ptr` zwraca obiekt, który odwołuje się do wyjątku SEH. Funkcja zgłasza wyjątek SEH, jeśli jest wywoływana z obiektem thetransported `exception_ptr` jako argumentem. `rethrow_exception`

`exception_ptr` Funkcja zwraca wartość null, jeśli wywołuje ją w obsłudze SEH __finally, __except lub wyrażenie filtru __except. `current_exception`

Transportowany wyjątek nie obsługuje wyjątków zagnieżdżonych. Wyjątek zagnieżdżony występuje, jeśli podczas obsługi wyjątku jest zgłaszany inny wyjątek. Jeśli przechwytywany jest wyjątek zagnieżdżony, `EXCEPTION_RECORD.ExceptionRecord` element członkowski danych wskazuje `EXCEPTION_RECORD` łańcuch struktur, które opisują skojarzone wyjątki. Funkcja `current_exception` nie obsługuje zagnieżdżonych wyjątków, ponieważ `exception_ptr` zwraca obiekt, którego `ExceptionRecord` składowa danych jest różna od zera.

W przypadku przechwycenia wyjątku SEH należy zarządzać pamięcią, do której odwołuje się dowolny `EXCEPTION_RECORD.ExceptionInformation` wskaźnik w tablicy elementów członkowskich danych. Należy zagwarantować, że pamięć jest prawidłowa w okresie istnienia odpowiedniego `exception_ptr` obiektu i że pamięć jest zwalniana `exception_ptr` po usunięciu obiektu.

Można użyć funkcji tłumacza wyjątków strukturalnych (SE) wraz z funkcją transportu wyjątków. Jeśli wyjątek SEH jest tłumaczony na C++ wyjątek, `current_exception` funkcja zwraca `exception_ptr` odwołanie odwołujące się do przetłumaczonego wyjątku zamiast oryginalnego wyjątku SEH. Następnie `rethrow_exception` funkcja zgłasza wyjątek przetłumaczony, a nie oryginalny wyjątek. Aby uzyskać więcej informacji na temat funkcji translatora SE, zobacz [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="rethrow_exception-function"></a>Funkcja rethrow_exception

Po przechowaniu przechwyconego wyjątku w `exception_ptr` obiekcie wątek główny może przetworzyć obiekt. W wątku podstawowym Wywołaj `rethrow_exception` funkcję razem `exception_ptr` z obiektem jako argumentem. Funkcja wyodrębnia wyjątek `exception_ptr` z obiektu, a następnie zgłasza wyjątek w kontekście wątku głównego. `rethrow_exception` Jeśli `rethrow_exception` parametr *p* funkcji ma wartość null `exception_ptr`, funkcja zgłasza [std:: bad_exception](../standard-library/bad-exception-class.md).

Wyodrębniony wyjątek jest teraz wyjątkiem bieżącym w wątku podstawowym i można go obsłużyć, podobnie jak w przypadku innych wyjątków. W przypadku przechwycenia wyjątku można go obsłużyć natychmiast lub użyć instrukcji **throw** , aby wysłać ją do programu obsługi wyjątków wyższego poziomu. W przeciwnym razie nic nie rób, niech domyślny program obsługi wyjątków systemu zakończy proces.

## <a name="make_exception_ptr-function"></a>Funkcja make_exception_ptr

Funkcja przyjmuje wystąpienie klasy jako argument, a następnie `exception_ptr` zwraca odwołanie odwołujące się do wystąpienia. `make_exception_ptr` Zazwyczaj należy określić obiekt [klasy wyjątku](../standard-library/exception-class.md) jako argument `make_exception_ptr` funkcji, chociaż każdy obiekt klasy może być argumentem.

`current_exception` `exception_ptr` C++ Wywołanie funkcji jest równoważne do zgłaszania wyjątku, przechwytywania go w bloku catch, a następnie wywołania funkcji zwracającej obiekt, który odwołuje się do wyjątku. `make_exception_ptr` Implementacja firmy Microsoft dla `make_exception_ptr` funkcji jest bardziej wydajna niż zgłaszanie i przechwytywanie wyjątku.

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

**Nagłówek:** \<> wyjątku

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)<br/>
[/EH (Model obsługi wyjątku)](../build/reference/eh-exception-handling-model.md)<br/>
[/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md)

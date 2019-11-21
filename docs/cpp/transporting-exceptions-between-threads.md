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
ms.openlocfilehash: 25b09c508b932a4d1470f6b23f03aa52e62c68cc
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246311"
---
# <a name="transporting-exceptions-between-threads"></a>Transport wyjątków między wątkami

The Microsoft C++ compiler (MSVC) supports *transporting an exception* from one thread to another. Transport wyjątków umożliwia przechwytywanie wyjątków w jednym wątku, a następnie powodowanie, aby były generowane w innym wątku. Na przykład, możesz użyć tej funkcji do pisania aplikacji wielowątkowych, gdzie wątek główny obsługuje wszystkie wyjątki generowane przez pomocnicze wątki. Transport wyjątków jest przydatny głównie dla deweloperów, którzy tworzą biblioteki lub systemy programowania równoległego. To implement transporting exceptions, MSVC provides the [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) type and the [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception), and [make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) functions.

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
|*unspecified*|An unspecified internal class that is used to implement the `exception_ptr` type.|
|*p*|An `exception_ptr` object that references an exception.|
|*E*|Klasa, która reprezentuje wyjątek.|
|*e*|An instance of the parameter `E` class.|

## <a name="return-value"></a>Return value

The `current_exception` function returns an `exception_ptr` object that references the exception that is currently in progress. If no exception is in progress, the function returns an `exception_ptr` object that is not associated with any exception.

The `make_exception_ptr` function returns an `exception_ptr` object that references the exception specified by the *e* parameter.

## <a name="remarks"></a>Uwagi

### <a name="scenario"></a>Scenariusz

Wyobraź sobie, że chcesz utworzyć aplikację, która może być skalowana, aby obsłużyć zmienną ilość pracy. Aby osiągnąć ten cel, projektujesz aplikację wielowątkową, gdzie wstępny, podstawowy wątek tworzy tyle wątków pomocniczych, ile potrzebuje, aby wykonać zadanie. Pomocnicze wątki pomagają wątkowi głównemu zarządzać zasobami, równoważyć obciążenia, a także zwiększać wydajność. Dzięki rozłożeniu pracy, aplikacja wielowątkowa działa lepiej niż aplikacja jednowątkowa.

Jednak jeśli wątek pomocniczy zgłasza wyjątek, wskazane jest, aby watek główny go obsłużył. To dlatego, że chcesz, aby aplikacja obsługiwała wyjątki w sposób spójny, jednolity, bez względu na liczbę wątków pomocniczych.

### <a name="solution"></a>Rozwiązanie

Aby obsłużyć poprzedni scenariusz, standard C++ obsługuje transportowanie wyjątków pomiędzy wątkami. If a secondary thread throws an exception, that exception becomes the *current exception*. By analogy to the real world, the current exception is said to be *in flight*. Bieżący wyjątek jest w locie od czasu, kiedy jest generowany, aż do momentu, gdy zostanie zwrócony przez kod obsługi wyjątków, który go przechwycił.

The secondary thread can catch the current exception in a **catch** block, and then call the `current_exception` function to store the exception in an `exception_ptr` object. The `exception_ptr` object must be available to the secondary thread and to the primary thread. For example, the `exception_ptr` object can be a global variable whose access is controlled by a mutex. The term *transport an exception* means an exception in one thread can be converted to a form that can be accessed by another thread.

Next, the primary thread calls the `rethrow_exception` function, which extracts and then throws the exception from the `exception_ptr` object. Wygenerowany wyjątek staje się bieżącym wyjątkiem w wątku głównym. Oznacza to, że wyjątek wygląda tak, jakby pochodził z wątku głównego.

Finally, the primary thread can catch the current exception in a **catch** block and then process it or throw it to a higher level exception handler. Lub wątek główny może zignorować wyjątek i pozwolić zakończyć proces.

Większość aplikacji nie musi transportować wyjątków między wątkami. Jednak ta funkcja jest przydatna w systemach przetwarzania równoległego, ponieważ system może podzielić pracę pomiędzy wątki pomocnicze, procesory lub rdzenie. W środowisku przetwarzania równoległego pojedynczy, wyspecjalizowany wątek może obsługiwać wszystkie wyjątki z pomocniczych wątków i może stanowić spójny model obsługi wyjątków dla innych aplikacji.

Aby uzyskać więcej informacji o propozycji komitetu standardów C++, znajdź w Internecie dokument o numerze N2179 pod tytułem „Language Support for Transporting Exceptions between Threads” (Obsługa języka dla transportu wyjątków między wątkami).

### <a name="exception-handling-models-and-compiler-options"></a>Exception-handling models and compiler options

Model obsługi wyjątków aplikacji określa, czy można przechwycić i transportować wyjątek. Visual C++ obsługuje trzy modele, które mogą obsługiwać wyjątki C++, obsługę wyjątków strukturalnych (SEH) i wyjątki środowiska uruchomieniowego języka wspólnego (CLR). Use the [/EH](../build/reference/eh-exception-handling-model.md) and [/clr](../build/reference/clr-common-language-runtime-compilation.md) compiler options to specify your application's exception-handling model.

Tylko następujące połączenie opcji kompilatora i instrukcji programowania może transportować wyjątek. Inne połączenia nie mogą przechwytywać wyjątków lub mogą je przechwytywać, ale nie transportować.

- The **/EHa** compiler option and the **catch** statement can transport SEH and C++ exceptions.

- The **/EHa**, **/EHs**, and **/EHsc** compiler options and the **catch** statement can transport C++ exceptions.

- The **/CLR** compiler option and the **catch** statement can transport C++ exceptions. The **/CLR** compiler option implies specification of the **/EHa** option. Należy zauważyć, że kompilator nie obsługuje transportowania wyjątków zarządzanych. This is because managed exceptions, which are derived from the [System.Exception class](../standard-library/exception-class.md), are already objects that you can move between threads by using the facilities of the common languange runtime.

   > [!IMPORTANT]
   > We recommend that you specify the **/EHsc** compiler option and catch only C++ exceptions. You expose yourself to a security threat if you use the **/EHa** or **/CLR** compiler option and a **catch** statement with an ellipsis *exception-declaration* (`catch(...)`). You probably intend to use the **catch** statement to capture a few specific exceptions. However, the `catch(...)` statement captures all C++ and SEH exceptions, including unexpected ones that should be fatal. Jeśli zignorujesz lub źle obsłużysz nieoczekiwany wyjątek, złośliwy kod wykorzystać tę szansę do obejścia zabezpieczeń programu.

## <a name="usage"></a>Użycie

The following sections describe how to transport exceptions by using the `exception_ptr` type, and the `current_exception`, `rethrow_exception`, and `make_exception_ptr` functions.

## <a name="exception_ptr-type"></a>exception_ptr type

Use an `exception_ptr` object to reference the current exception or an instance of a user-specified exception. In the Microsoft implementation, an exception is represented by an [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) structure. Each `exception_ptr` object includes an exception reference field that points to a copy of the `EXCEPTION_RECORD` structure that represents the exception.

When you declare an `exception_ptr` variable, the variable is not associated with any exception. To znaczy, że pole odwołania wyjątku ma wartość NULL. Such an `exception_ptr` object is called a *null exception_ptr*.

Use the `current_exception` or `make_exception_ptr` function to assign an exception to an `exception_ptr` object. When you assign an exception to an `exception_ptr` variable, the variable's exception reference field points to a copy of the exception. If there is insufficient memory to copy the exception, the exception reference field points to a copy of a [std::bad_alloc](../standard-library/bad-alloc-class.md) exception. If the `current_exception` or `make_exception_ptr` function cannot copy the exception for any other reason, the function calls the [terminate](../c-runtime-library/reference/terminate-crt.md) function to exit the current process.

Despite its name, an `exception_ptr` object is not itself a pointer. It does not obey pointer semantics and cannot be used with the pointer member access (`->`) or indirection (`*`) operators. The `exception_ptr` object has no public data members or member functions.

### <a name="comparisons"></a>Porównania

You can use the equal (`==`) and not-equal (`!=`) operators to compare two `exception_ptr` objects. The operators do not compare the binary value (bit pattern) of the `EXCEPTION_RECORD` structures that represent the exceptions. Instead, the operators compare the addresses in the exception reference field of the `exception_ptr` objects. Consequently, a null `exception_ptr` and the NULL value compare as equal.

## <a name="current_exception-function"></a>current_exception function

Call the `current_exception` function in a **catch** block. If an exception is in flight and the **catch** block can catch the exception, the `current_exception` function returns an `exception_ptr` object that references the exception. Otherwise, the function returns a null `exception_ptr` object.

### <a name="details"></a>Szczegóły

The `current_exception` function captures the exception that is in flight regardless of whether the **catch** statement specifies an [exception-declaration](../cpp/try-throw-and-catch-statements-cpp.md) statement.

The destructor for the current exception is called at the end of the **catch** block if you do not rethrow the exception. However, even if you call the `current_exception` function in the destructor, the function returns an `exception_ptr` object that references the current exception.

Successive calls to the `current_exception` function return `exception_ptr` objects that refer to different copies of the current exception. W związku z tym obiekty są porównane jako nierówne, ponieważ odnoszą się one do poszczególnych kopii, mimo że kopie mają tę samą wartość binarną.

### <a name="seh-exceptions"></a>SEH exceptions

If you use the **/EHa** compiler option, you can catch an SEH exception in a C++ **catch** block. The `current_exception` function returns an `exception_ptr` object that references the SEH exception. And the `rethrow_exception` function throws the SEH exception if you call it with thetransported `exception_ptr` object as its argument.

The `current_exception` function returns a null `exception_ptr` if you call it in an SEH **__finally** termination handler, an **__except** exception handler, or the **__except** filter expression.

Transportowany wyjątek nie obsługuje wyjątków zagnieżdżonych. Wyjątek zagnieżdżony występuje, jeśli podczas obsługi wyjątku jest zgłaszany inny wyjątek. If you catch a nested exception, the `EXCEPTION_RECORD.ExceptionRecord` data member points to a chain of `EXCEPTION_RECORD` structures that describe the associated exceptions. The `current_exception` function does not support nested exceptions because it returns an `exception_ptr` object whose `ExceptionRecord` data member is zeroed out.

If you catch an SEH exception, you must manage the memory referenced by any pointer in the `EXCEPTION_RECORD.ExceptionInformation` data member array. You must guarantee that the memory is valid during the lifetime of the corresponding `exception_ptr` object, and that the memory is freed when the `exception_ptr` object is deleted.

Można użyć funkcji tłumacza wyjątków strukturalnych (SE) wraz z funkcją transportu wyjątków. If an SEH exception is translated to a C++ exception, the `current_exception` function returns an `exception_ptr` that references the translated exception instead of the original SEH exception. The `rethrow_exception` function subsequently throws the translated exception, not the original exception. For more information about SE translator functions, see [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="rethrow_exception-function"></a>rethrow_exception function

After you store a caught exception in an `exception_ptr` object, the primary thread can process the object. In your primary thread, call the `rethrow_exception` function together with the `exception_ptr` object as its argument. The `rethrow_exception` function extracts the exception from the `exception_ptr` object and then throws the exception in the context of the primary thread. If the *p* parameter of the `rethrow_exception` function is a null `exception_ptr`, the function throws [std::bad_exception](../standard-library/bad-exception-class.md).

Wyodrębniony wyjątek jest teraz wyjątkiem bieżącym w wątku podstawowym i można go obsłużyć, podobnie jak w przypadku innych wyjątków. If you catch the exception, you can handle it immediately or use a **throw** statement to send it to a higher level exception handler. W przeciwnym razie nic nie rób, niech domyślny program obsługi wyjątków systemu zakończy proces.

## <a name="make_exception_ptr-function"></a>make_exception_ptr, funkcja

The `make_exception_ptr` function takes an instance of a class as its argument and then returns an `exception_ptr` that references the instance. Usually, you specify an [exception class](../standard-library/exception-class.md) object as the argument to the `make_exception_ptr` function, although any class object can be the argument.

Calling the `make_exception_ptr` function is equivalent to throwing a C++ exception, catching it in a **catch** block, and then calling the `current_exception` function to return an `exception_ptr` object that references the exception. The Microsoft implementation of the `make_exception_ptr` function is more efficient than throwing and then catching an exception.

An application typically does not require the `make_exception_ptr` function, and we discourage its use.

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

**Header:** \<exception>

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)<br/>
[/EH (Model obsługi wyjątku)](../build/reference/eh-exception-handling-model.md)<br/>
[/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md)

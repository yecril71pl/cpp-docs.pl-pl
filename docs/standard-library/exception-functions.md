---
title: '&lt;&gt;funkcje wyjątków'
ms.date: 11/04/2016
f1_keywords:
- exception/std::current_exception
- exception/std::get_terminate
- exception/std::get_unexpected
- exception/std::make_exception_ptr
- exception/std::rethrow_exception
- exception/std::set_terminate
- exception/std::set_unexpected
- exception/std::terminate
- exception/std::uncaught_exception
- exception/std::unexpected
ms.assetid: c09ac569-5e35-4fe8-872d-ca5810274dd7
helpviewer_keywords:
- std::current_exception [C++]
- std::get_terminate [C++]
- std::get_unexpected [C++]
- std::make_exception_ptr [C++]
- std::rethrow_exception [C++]
- std::set_terminate [C++]
- std::set_unexpected [C++]
- std::terminate [C++]
- std::uncaught_exception [C++]
- std::unexpected [C++]
ms.openlocfilehash: 849f3c8406c43b0efc2d34837e00fee6ff64e52a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193786"
---
# <a name="ltexceptiongt-functions"></a>&lt;&gt;funkcje wyjątków

## <a name="current_exception"></a><a name="current_exception"></a>current_exception

Uzyskuje inteligentny wskaźnik na bieżący wyjątek.

```cpp
exception_ptr current_exception();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) wskazujący na bieżący wyjątek.

### <a name="remarks"></a>Uwagi

Wywołaj `current_exception` funkcję w bloku catch. Jeśli wyjątek jest w locie i blok catch może przechwycić wyjątek, `current_exception` Funkcja zwraca `exception_ptr` obiekt, który odwołuje się do wyjątku. W przeciwnym razie funkcja zwraca obiekt o wartości null `exception_ptr` .

`current_exception`Funkcja przechwytuje wyjątek, który jest w locie, niezależnie od tego, czy **`catch`** instrukcja określa instrukcję [deklaracji wyjątku](../cpp/try-throw-and-catch-statements-cpp.md) .

Destruktor dla bieżącego wyjątku jest wywoływany na końcu **`catch`** bloku, jeśli nie zostanie ponownie zgłoszony wyjątek. Jednak nawet w przypadku wywołania `current_exception` funkcji w destruktorze funkcja zwraca `exception_ptr` obiekt, który odwołuje się do bieżącego wyjątku.

Kolejne wywołania `current_exception` funkcji zwracają `exception_ptr` obiekty odwołujące się do różnych kopii bieżącego wyjątku. W związku z tym obiekty są porównane jako nierówne, ponieważ odnoszą się one do poszczególnych kopii, mimo że kopie mają tę samą wartość binarną.

## <a name="make_exception_ptr"></a><a name="make_exception_ptr"></a>make_exception_ptr

Tworzy obiekt [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) , który przechowuje kopię wyjątku.

```cpp
template <class E>
    exception_ptr make_exception_ptr(E Except);
```

### <a name="parameters"></a>Parametry

*Ale*\
Klasa z wyjątkiem do skopiowania. Zazwyczaj należy określić obiekt [klasy wyjątku](../standard-library/exception-class.md) jako argument `make_exception_ptr` funkcji, chociaż każdy obiekt klasy może być argumentem.

### <a name="return-value"></a>Wartość zwracana

Obiekt [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) wskazujący kopię bieżącego wyjątku dla programu *z wyjątkiem*.

### <a name="remarks"></a>Uwagi

Wywołanie `make_exception_ptr` funkcji jest równoznaczne z wygenerowaniem wyjątku C++, przechwyceniem go w bloku catch, a następnie wywołaniem funkcji [current_exception](../standard-library/exception-functions.md#current_exception) w celu zwrócenia `exception_ptr` obiektu, który odwołuje się do wyjątku. Implementacja firmy Microsoft dla `make_exception_ptr` funkcji jest bardziej wydajna niż zgłaszanie i przechwytywanie wyjątku.

Aplikacja zwykle nie wymaga `make_exception_ptr` funkcji i odradza jej używanie.

## <a name="rethrow_exception"></a><a name="rethrow_exception"></a>rethrow_exception

Zgłasza wyjątek przekazany jako parametr.

```cpp
void rethrow_exception(exception_ptr P);
```

### <a name="parameters"></a>Parametry

*St*\
Przechwycony wyjątek do ponownego zgłoszenia. Jeśli *P* jest [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)o wartości null, funkcja zgłasza [std:: bad_exception](../standard-library/bad-exception-class.md).

### <a name="remarks"></a>Uwagi

Po przechowaniu przechwyconego wyjątku w `exception_ptr` obiekcie wątek główny może przetworzyć obiekt. W wątku podstawowym Wywołaj `rethrow_exception` funkcję razem z `exception_ptr` obiektem jako argumentem. `rethrow_exception`Funkcja wyodrębnia wyjątek z `exception_ptr` obiektu, a następnie zgłasza wyjątek w kontekście wątku głównego.

## <a name="get_terminate"></a><a name="get_terminate"></a>get_terminate

Uzyskuje bieżącą `terminate_handler` funkcję.

```cpp
terminate_handler get_terminate();
```

## <a name="set_terminate"></a><a name="set_terminate"></a>set_terminate

Ustanawia nowy `terminate_handler` , który zostanie wywołany po zakończeniu działania programu.

```cpp
terminate_handler set_terminate(terminate_handler fnew) throw();
```

### <a name="parameters"></a>Parametry

*fnew*\
Funkcja, która ma zostać wywołana po zakończeniu.

### <a name="return-value"></a>Wartość zwracana

Adres poprzedniej funkcji, która została wywołana po zakończeniu.

### <a name="remarks"></a>Uwagi

Funkcja ustanowi nowe [terminate_handler](../standard-library/exception-typedefs.md#terminate_handler) jako funkcja * *fnew*. W ten sposób *fnew* nie może być pustym wskaźnikiem. Funkcja zwraca adres poprzedniej procedury obsługi zakończenia.

### <a name="example"></a>Przykład

```cpp
// exception_set_terminate.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void termfunction()
{
    cout << "My terminate function called." << endl;
    abort();
}

int main()
{
    terminate_handler oldHandler = set_terminate(termfunction);

    // Throwing an unhandled exception would also terminate the program
    // or we could explicitly call terminate();

    //throw bad_alloc();
    terminate();
}
```

## <a name="get_unexpected"></a><a name="get_unexpected"></a>get_unexpected

Uzyskuje bieżącą `unexpected_handler` funkcję.

```cpp
unexpected_handler get_unexpected();
```

## <a name="rethrow_if_nested"></a><a name="rethrow_if_nested"></a>rethrow_if_nested

```cpp
template <class E>
    void rethrow_if_nested(const E& e);
```

### <a name="remarks"></a>Uwagi

Jeśli nie jest to typ klasy polimorficznej lub jeśli `nested_exception` jest niedostępny lub niejednoznaczny, nie ma żadnego efektu. W przeciwnym razie wykonuje dynamiczne rzutowanie.

## <a name="set_unexpected"></a><a name="set_unexpected"></a>set_unexpected

Ustanawia nowy, `unexpected_handler` gdy zostanie napotkany nieoczekiwany wyjątek.

```cpp
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```

### <a name="parameters"></a>Parametry

*fnew*\
Funkcja, która ma zostać wywołana w przypadku napotkania nieoczekiwanego wyjątku.

### <a name="return-value"></a>Wartość zwracana

Adres poprzedniego `unexpected_handler` .

### <a name="remarks"></a>Uwagi

*fnew* nie może być pustym wskaźnikiem.

Standard C++ wymaga, że `unexpected` jest wywoływana, gdy funkcja zgłasza wyjątek, który nie znajduje się na liście throw. Bieżąca implementacja nie obsługuje tej funkcji. Poniższy przykład wywołuje `unexpected` bezpośrednio, który następnie wywołuje `unexpected_handler` .

### <a name="example"></a>Przykład

```cpp
// exception_set_unexpected.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void uefunction()
{
    cout << "My unhandled exception function called." << endl;
    terminate(); // this is what unexpected() calls by default
}

int main()
{
    unexpected_handler oldHandler = set_unexpected(uefunction);

    unexpected(); // library function to force calling the
                  // current unexpected handler
}
```

## <a name="terminate"></a><a name="terminate"></a>kończyć

Wywołuje terminate_handler.

```cpp
void terminate();
```

### <a name="remarks"></a>Uwagi

Funkcja wywołuje procedurę obsługi zakończenia, funkcję typu **`void`** . Jeśli `terminate` jest wywoływana bezpośrednio przez program, procedura obsługi zakończenia jest ostatnim ustawieniem przez wywołanie do [set_terminate](../standard-library/exception-functions.md#set_terminate). Jeśli `terminate` jest wywoływana dla którejkolwiek z kilku innych przyczyn podczas obliczania wyrażenia throw, procedura obsługi zakończenia jest taka, która obowiązuje natychmiast po obliczeniu wyrażenia throw.

Procedura obsługi zakończenia nie może powrócić do jego obiektu wywołującego. W trakcie uruchamiania programu program obsługi kończy działanie `abort` .

### <a name="example"></a>Przykład

Zobacz [set_unexpected](../standard-library/exception-functions.md#set_unexpected) , aby zapoznać się z przykładem użycia `terminate` .

## <a name="throw_with_nested"></a><a name="throw_with_nested"></a>throw_with_nested

```cpp
template <class T> [[noreturn]]
    void throw_with_nested(T&& t);
```

### <a name="remarks"></a>Uwagi

Zgłasza wyjątek z zagnieżdżonymi wyjątkami.

## <a name="uncaught_exception"></a><a name="uncaught_exception"></a>uncaught_exception

Zwraca **`true`** tylko wtedy, gdy zgłoszony wyjątek jest aktualnie przetwarzany.

```cpp
bool uncaught_exception();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca **`true`** po zakończeniu obliczania wyrażenia throw oraz przed ukończeniem inicjalizacji deklaracji wyjątku w procedurze obsługi dopasowania lub wywołując [nieoczekiwany](../standard-library/exception-functions.md#unexpected) wynik w wyniku wyrażenia throw. W szczególności `uncaught_exception` zwróci **`true`** wartość po wywołaniu z destruktora, który jest wywoływany podczas operacji unwindy wyjątku. Na urządzeniach `uncaught_exception` jest obsługiwana tylko w Windows CE 5,00 i nowszych wersjach, w tym na platformach Windows Mobile 2005.

### <a name="example"></a>Przykład

```cpp
// exception_uncaught_exception.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>
#include <string>

class Test
{
public:
   Test( std::string msg ) : m_msg( msg )
   {
      std::cout << "In Test::Test(\"" << m_msg << "\")" << std::endl;
   }
   ~Test( )
   {
      std::cout << "In Test::~Test(\"" << m_msg << "\")" << std::endl
         << "        std::uncaught_exception( ) = "
         << std::uncaught_exception( )
         << std::endl;
   }
private:
    std::string m_msg;
};

// uncaught_exception will be true in the destructor
// for the object created inside the try block because
// the destructor is being called as part of the unwind.

int main( void )
   {
      Test t1( "outside try block" );
      try
      {
         Test t2( "inside try block" );
         throw 1;
      }
      catch (...) {
   }
}
```

```Output
In Test::Test("outside try block")
In Test::Test("inside try block")
In Test::~Test("inside try block")
        std::uncaught_exception( ) = 1
In Test::~Test("outside try block")
        std::uncaught_exception( ) = 0
```

## <a name="unexpected"></a><a name="unexpected"></a>oczekiwan

Wywołuje nieoczekiwaną procedurę obsługi.

```cpp
void unexpected();
```

### <a name="remarks"></a>Uwagi

Standard C++ wymaga, że `unexpected` jest wywoływana, gdy funkcja zgłasza wyjątek, który nie znajduje się na liście throw. Bieżąca implementacja nie obsługuje tej funkcji. Przykład wywołuje `unexpected` bezpośrednio, który wywołuje nieoczekiwaną procedurę obsługi.

Funkcja wywołuje nieoczekiwaną procedurę obsługi, funkcję typu **`void`** . Jeśli `unexpected` jest wywoływana bezpośrednio przez program, nieoczekiwany program obsługi jest ostatnim ustawieniem przez wywołanie do [set_unexpected](../standard-library/exception-functions.md#set_unexpected).

Nieoczekiwany program obsługi nie może powrócić do jego obiektu wywołującego. Może zakończyć wykonywanie przez:

- Zgłaszanie obiektu typu wymienionego w specyfikacji wyjątku lub obiektu dowolnego typu, jeśli nieoczekiwana procedura obsługi jest wywoływana bezpośrednio przez program.

- Zgłaszanie obiektu typu [bad_exception](../standard-library/bad-exception-class.md).

- Wywołanie [terminate](../standard-library/exception-functions.md#terminate)metody Terminate `abort` lub `exit` .

Podczas uruchamiania programu nieoczekiwana procedura obsługi jest funkcją, która wywołuje [przerwanie](../standard-library/exception-functions.md#terminate).

### <a name="example"></a>Przykład

Zobacz [set_unexpected](../standard-library/exception-functions.md#set_unexpected) , aby zapoznać się z przykładem użycia `unexpected` .

---
title: '&lt;wyjątek&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 4aab46fa771b88d1baad311aa631a57afce4911e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ltexceptiongt-functions"></a>&lt;wyjątek&gt; funkcji

||||
|-|-|-|
|[current_exception](#current_exception)|[get_terminate](#get_terminate)|[get_unexpected](#get_unexpected)|
|[make_exception_ptr](#make_exception_ptr)|[rethrow_exception](#rethrow_exception)|[set_terminate —](#set_terminate)|
|[set_unexpected](#set_unexpected)|[Zakończenie](#terminate)|[uncaught_exception](#uncaught_exception)|
|[Nieoczekiwany](#unexpected)|

## <a name="current_exception"></a>  current_exception

Uzyskuje inteligentny wskaźnik na bieżący wyjątek.

```cpp
exception_ptr current_exception();
```

### <a name="return-value"></a>Wartość zwracana

[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) obiektu wskazuje bieżący wyjątek.

### <a name="remarks"></a>Uwagi

Wywołanie `current_exception` funkcji w bloku catch. Jeśli wyjątek jest transmitowane i bloku catch można przechwytywać elementu exception, `current_exception` funkcja zwraca `exception_ptr` obiektu, który odwołuje się do wyjątku. W przeciwnym razie funkcja zwraca wartość null `exception_ptr` obiektu.

`current_exception` Funkcja przechwytuje wyjątek, który są przesyłane niezależnie od tego, czy `catch` określa instrukcji [deklaracji wyjątku](../cpp/try-throw-and-catch-statements-cpp.md) instrukcji.

Destruktor dla bieżącego wyjątku jest wywoływana po zakończeniu `catch` zablokować, jeśli nie ponownie Zgłoś wyjątek. Jednak nawet wtedy, gdy jest wywoływana `current_exception` działać w destruktor, funkcja zwraca `exception_ptr` obiektu, który odwołuje się do bieżącego wyjątku.

Kolejne wywołania `current_exception` funkcji powrotu `exception_ptr` obiekty, które odwołują się do różnych kopii bieżącego wyjątku. W związku z tym obiekty są porównane jako nierówne, ponieważ odnoszą się one do poszczególnych kopii, mimo że kopie mają tę samą wartość binarną.

## <a name="make_exception_ptr"></a>  make_exception_ptr

Tworzy [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) obiekt przechowujący kopię Wystąpił wyjątek.

```cpp
template <class E>
exception_ptr make_exception_ptr(E Except);
```

### <a name="parameters"></a>Parametry

`Except` Klasa wyjątku do skopiowania. Zwykle, określ [klasy wyjątku](../standard-library/exception-class.md) obiektu jako argument `make_exception_ptr` działanie, mimo że dowolny obiekt klasy może być argumentem.

### <a name="return-value"></a>Wartość zwracana

[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) wskazujący kopię bieżącego wyjątku dla obiekt `Except`.

### <a name="remarks"></a>Uwagi

Wywoływanie `make_exception_ptr` funkcji jest odpowiednikiem zgłaszanie wyjątków C++, im w bloku catch, a następnie wywołując [current_exception](../standard-library/exception-functions.md#current_exception) funkcja zwracająca `exception_ptr` obiektu, który odwołuje się do wyjątku. Implementacja firmy Microsoft `make_exception_ptr` funkcja jest bardziej efektywne niż zgłaszanie, a następnie przechwytywanie wyjątku.

Zwykle nie wymaga aplikacji `make_exception_ptr` funkcji i firma Microsoft zniechęcić jej użycia.

## <a name="rethrow_exception"></a>  rethrow_exception

Zgłasza wyjątek przekazany jako parametr.

```cpp
void rethrow_exception(exception_ptr P);
```

### <a name="parameters"></a>Parametry

`P` Zgłoszony wyjątek, aby zgłosić ponownie. Jeśli `P` ma wartość null [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr), funkcja zwraca [std::bad_exception](../standard-library/bad-exception-class.md).

### <a name="remarks"></a>Uwagi

Po przechowywania zgłoszony wyjątek w `exception_ptr` obiekt podstawowy wątku można przetworzyć obiektu. W sieci podstawowej wątku wywołać `rethrow_exception` działają razem z `exception_ptr` obiektu jako jej argument. `rethrow_exception` Funkcja wyodrębnia wyjątku z `exception_ptr` obiekt, a następnie zgłasza wyjątek w kontekście podstawowy wątku.

## <a name="get_terminate"></a>  get_terminate —

Pobiera bieżący `terminate_handler` funkcji.

```cpp
terminate_handler get_terminate();
```

## <a name="set_terminate"></a>  set_terminate —

Określa nową `terminate_handler` ma być wywoływana po zakończeniu programu.

```cpp
terminate_handler set_terminate(terminate_handler fnew) throw();
```

### <a name="parameters"></a>Parametry

`fnew` Funkcja wywoływana po zakończeniu.

### <a name="return-value"></a>Wartość zwracana

Adres funkcji poprzednie używany do wywołania po zakończeniu.

### <a name="remarks"></a>Uwagi

Funkcja ustanawia nowego [terminate_handler](../standard-library/exception-typedefs.md#terminate_handler) jako funkcja * `fnew`. W związku z tym `fnew` nie może mieć pustego wskaźnika. Funkcja zwraca adres poprzedniego zakończenie obsługi.

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

## <a name="get_unexpected"></a>  get_unexpected —

Pobiera bieżący `unexpected_handler` funkcji.

```cpp
unexpected_handler get_unexpected();
```

## <a name="set_unexpected"></a>  set_unexpected —

Określa nową `unexpected_handler` się po wystąpił nieoczekiwany wyjątek napotkano.

```cpp
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```

### <a name="parameters"></a>Parametry

`fnew` Funkcja wywoływana, gdy Napotkano nieoczekiwany wyjątek.

### <a name="return-value"></a>Wartość zwracana

Adres poprzedniego `unexpected_handler`.

### <a name="remarks"></a>Uwagi

`fnew` nie może mieć pustego wskaźnika.

C++ Standard wymaga, aby `unexpected` jest wywoływane, gdy funkcja zwraca wyjątek, który nie znajduje się na liście throw. Bieżąca implementacja nie obsługuje to. Następujące przykładowe wywołania `unexpected` bezpośrednio, które następnie wywołuje `unexpected_handler`.

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

## <a name="terminate"></a>  Zakończenie

Wywołuje terminate_handler.

```cpp
void terminate();
```

### <a name="remarks"></a>Uwagi

Funkcja wywołuje program obsługi przerwania, funkcja typu `void`. Jeśli **przerwania** jest wywoływana bezpośrednio przez program obsługi przerwania jest jeden ostatnio ustawiony przez wywołanie do [set_terminate —](../standard-library/exception-functions.md#set_terminate). Jeśli **przerwania** jest wywoływana dla każdej z kilku powodów podczas obliczania wyrażenia throw obsługi przerwania jest obowiązywać natychmiast po przeprowadzeniu oceny wyrażenia throw.

Program obsługi przerwania nie może zwracać do swojego obiektu wywołującego. Przy uruchamianiu programu obsługi przerwania jest funkcją, która wywołuje **przerwania**.

### <a name="example"></a>Przykład

Zobacz [set_unexpected —](../standard-library/exception-functions.md#set_unexpected) na przykład użycie **przerwanie**.

## <a name="uncaught_exception"></a>  uncaught_exception

Zwraca `true` tylko wtedy, gdy zwrócony wyjątek jest obecnie przetwarzana w.

```cpp
bool uncaught_exception();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `true` po zakończeniu oceny wyrażenia throw i przed zakończeniem inicjowania deklaracji wyjątku w odpowiadającą jej instrukcją obsługi lub wywoływania [nieoczekiwany](../standard-library/exception-functions.md#unexpected) wyniku wyrażenia throw. W szczególności `uncaught_exception` zwróci `true` przy wywołaniach z destruktora jest wywoływana podczas unwind wyjątku. Na urządzeniach `uncaught_exception` jest obsługiwana tylko na Windows CE 5.00 i w nowszych wersjach, w tym platform Windows Mobile 2005.

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

## <a name="unexpected"></a>  Nieoczekiwany

Wywołuje program obsługi nieoczekiwany.

```cpp
void unexpected();
```

### <a name="remarks"></a>Uwagi

C++ Standard wymaga, aby `unexpected` jest wywoływane, gdy funkcja zwraca wyjątek, który nie znajduje się na liście throw. Bieżąca implementacja nie obsługuje to. Przykład wywołania `unexpected` bezpośrednio, które wywołuje program obsługi nieoczekiwany.

Nieoczekiwany obsługi funkcji typu wywołuje funkcję `void`. Jeśli `unexpected` jest wywoływana bezpośrednio przez program obsługi nieoczekiwany jest jeden ostatnio ustawiony przez wywołanie do [set_unexpected —](../standard-library/exception-functions.md#set_unexpected).

Nieoczekiwany obsługi nie może zwracać do swojego obiektu wywołującego. Może on zakończyć wykonywania przez:

- Zgłaszanie obiektu typu wymienione w specyfikacji wyjątku lub obiekt dowolnego typu, jeśli nieoczekiwany program obsługi zostanie wywołany bezpośrednio przez program.

- Wyrzucanie typu obiektu [bad_exception —](../standard-library/bad-exception-class.md).

- Wywoływanie [przerwanie](../standard-library/exception-functions.md#terminate), **przerwać** lub **zakończyć**( `int`).

Przy uruchamianiu programu obsługi nieoczekiwany to funkcja, która wywołuje [przerwanie](../standard-library/exception-functions.md#terminate).

### <a name="example"></a>Przykład

Zobacz [set_unexpected —](../standard-library/exception-functions.md#set_unexpected) na przykład użycie **nieoczekiwany.**

## <a name="see-also"></a>Zobacz także

[\<wyjątku >](../standard-library/exception.md)<br/>

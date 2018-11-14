---
title: '&lt;wyjątek&gt; funkcji'
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
ms.openlocfilehash: 22c5b34f1c87d10b48a797229bc987305fca8f9d
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523666"
---
# <a name="ltexceptiongt-functions"></a>&lt;wyjątek&gt; funkcji

||||
|-|-|-|
|[current_exception](#current_exception)|[get_terminate](#get_terminate)|[get_unexpected](#get_unexpected)|
|[make_exception_ptr](#make_exception_ptr)|[rethrow_exception](#rethrow_exception)|[set_terminate](#set_terminate)|
|[set_unexpected](#set_unexpected)|[Zakończenie](#terminate)|[uncaught_exception](#uncaught_exception)|
|[Nieoczekiwany](#unexpected)|

## <a name="current_exception"></a>  current_exception

Uzyskuje inteligentny wskaźnik na bieżący wyjątek.

```cpp
exception_ptr current_exception();
```

### <a name="return-value"></a>Wartość zwracana

[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) wskazujący na bieżący wyjątek.

### <a name="remarks"></a>Uwagi

Wywołaj `current_exception` funkcji w bloku catch. Jeśli wyjątek jest w locie i blok catch może przechwycić wyjątek, `current_exception` funkcja zwraca `exception_ptr` obiekt, który odwołuje się do wyjątku. W przeciwnym razie funkcja zwraca wartość null `exception_ptr` obiektu.

`current_exception` Funkcja przechwytuje wyjątek, który jest w locie, niezależnie od tego, czy **catch** instrukcja Określa [deklaracji wyjątku](../cpp/try-throw-and-catch-statements-cpp.md) instrukcji.

Destruktor dla bieżącego wyjątku jest wywoływany pod koniec **catch** zablokować, jeśli nie jest ponownie zgłaszany wyjątek. Jednak nawet wtedy, gdy wywołujesz `current_exception` funkcji w destruktorze, funkcja zwraca `exception_ptr` obiektu, który odwołuje się do bieżącego wyjątku.

Kolejne wywołania `current_exception` funkcji powrotu `exception_ptr` obiekty, które odwołują się do różnych kopii bieżącego wyjątku. W związku z tym obiekty są porównane jako nierówne, ponieważ odnoszą się one do poszczególnych kopii, mimo że kopie mają tę samą wartość binarną.

## <a name="make_exception_ptr"></a>  make_exception_ptr

Tworzy [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) obiekt, który przechowuje kopię wyjątku.

```cpp
template <class E>
exception_ptr make_exception_ptr(E Except);
```

### <a name="parameters"></a>Parametry

*Z wyjątkiem*<br/>
Klasa z wyjątkiem do skopiowania. Zwykle określaj [klasy wyjątku](../standard-library/exception-class.md) obiekt jako argument `make_exception_ptr` funkcji, mimo że dowolny obiekt klasy może być argumentem.

### <a name="return-value"></a>Wartość zwracana

[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) wskazujące na kopię bieżącego wyjątku dla *z wyjątkiem*.

### <a name="remarks"></a>Uwagi

Wywoływanie `make_exception_ptr` funkcji jest odpowiednikiem zgłaszania wyjątku C++, przechwytywania go w bloku catch, a następnie wywoływania [current_exception](../standard-library/exception-functions.md#current_exception) funkcja zwraca `exception_ptr` obiekt, który odwołuje się do wyjątku. Implementacja firmy Microsoft `make_exception_ptr` jest bardziej efektywna niż generowanie i następnie przechwytywanie wyjątku.

Aplikacja zazwyczaj nie wymaga `make_exception_ptr` funkcji, a my odradzamy jej użycie.

## <a name="rethrow_exception"></a>  rethrow_exception

Zgłasza wyjątek przekazany jako parametr.

```cpp
void rethrow_exception(exception_ptr P);
```

### <a name="parameters"></a>Parametry

*P*<br/>
Przechwycony wyjątek do ponownego zgłoszenia. Jeśli *P* ma wartość null [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr), funkcja zgłasza [std::bad_exception](../standard-library/bad-exception-class.md).

### <a name="remarks"></a>Uwagi

Po zapisaniu przechwyconego wyjątku w `exception_ptr` obiektu, wątek główny może przetworzyć obiekt. W podstawowym wątku, wywołaj `rethrow_exception` działać razem z `exception_ptr` obiekt jako argumentu. `rethrow_exception` Funkcja wyodrębnia wyjątek z `exception_ptr` obiektu i następnie zgłasza wyjątek w kontekście wątku głównego.

## <a name="get_terminate"></a>  get_terminate —

Uzyskuje bieżącą `terminate_handler` funkcji.

```cpp
terminate_handler get_terminate();
```

## <a name="set_terminate"></a>  set_terminate

Ustanawia nowy `terminate_handler` wywoływany przy zakończeniu programu.

```cpp
terminate_handler set_terminate(terminate_handler fnew) throw();
```

### <a name="parameters"></a>Parametry

*fnew*<br/>
Funkcja wywoływana po zakończeniu.

### <a name="return-value"></a>Wartość zwracana

Adres funkcji poprzednie używane do wywołania po zakończeniu.

### <a name="remarks"></a>Uwagi

Funkcja ustanawia nowy [terminate_handler](../standard-library/exception-typedefs.md#terminate_handler) jako funkcja * *fnew*. W efekcie *fnew* nie musi być wskaźnikiem typu null. Funkcja zwraca adres poprzedniej procedury obsługi zakończenia.

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

Uzyskuje bieżącą `unexpected_handler` funkcji.

```cpp
unexpected_handler get_unexpected();
```

## <a name="set_unexpected"></a>  set_unexpected

Ustanawia nowy `unexpected_handler` się kiedy napotkane nieoczekiwane wyjątki.

```cpp
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```

### <a name="parameters"></a>Parametry

*fnew*<br/>
Funkcja wywoływana, gdy Napotkano nieoczekiwany wyjątek.

### <a name="return-value"></a>Wartość zwracana

Adres poprzedniego `unexpected_handler`.

### <a name="remarks"></a>Uwagi

*fnew* nie musi być wskaźnikiem typu null.

C++ Standard wymaga, aby `unexpected` jest wywoływana, gdy funkcja zgłasza wyjątek, który nie znajduje się na swojej liście throw. Bieżąca implementacja nie obsługuje tego. Poniższy przykład wywołuje `unexpected` bezpośrednio, która następnie wywołuje metodę `unexpected_handler`.

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

Funkcja wywołuje terminate_handler, funkcja typu **void**. Jeśli `terminate` jest wywoływany bezpośrednio przez program obsługi przerwania jest ten, który ostatnio ustawiony przez wywołanie [set_terminate](../standard-library/exception-functions.md#set_terminate). Jeśli `terminate` jest wywoływana dla dowolnego z kilku powodów podczas obliczania wyrażenia throw, program obsługi zakończenia jest obowiązywać natychmiast po przeprowadzeniu oceny wyrażenia throw.

Program obsługi zakończenia nie może zwrócić do obiektu wywołującego. W momencie uruchamiania programu obsługi zakończenia jest funkcją, która wywołuje `abort`.

### <a name="example"></a>Przykład

Zobacz [set_unexpected](../standard-library/exception-functions.md#set_unexpected) przykładem użycia `terminate`.

## <a name="uncaught_exception"></a>  uncaught_exception

Zwraca **true** tylko wtedy, gdy zgłoszony wyjątek jest obecnie przetwarzany.

```cpp
bool uncaught_exception();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca **true** po ukończeniu oceny wyrażenia throw i przed ukończeniem zainicjowanie deklaracji wyjątku w pasującego obsługi lub wywoływania [nieoczekiwany](../standard-library/exception-functions.md#unexpected) na wyrażenie throw. W szczególności `uncaught_exception` zwróci **true** gdy wywoływana z destruktora, która jest wywoływana podczas odwijania wyjątku. Na urządzeniach `uncaught_exception` jest obsługiwana tylko na Windows CE 5.00 i nowsze wersje, łącznie z platform Windows Mobile 2005.

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

Wywołuje program obsługi nieoczekiwanych wyjątków.

```cpp
void unexpected();
```

### <a name="remarks"></a>Uwagi

C++ Standard wymaga, aby `unexpected` jest wywoływana, gdy funkcja zgłasza wyjątek, który nie znajduje się na swojej liście throw. Bieżąca implementacja nie obsługuje tego. Przykład wywołuje `unexpected` bezpośrednio, które wywołuje program obsługi nieoczekiwanych wyjątków.

Funkcja wywołuje program obsługi nieoczekiwanych wyjątków, funkcja typu **void**. Jeśli `unexpected` jest wywoływany bezpośrednio przez program obsługi nieoczekiwanych ten, który ostatnio ustawiono przez wywołanie [set_unexpected](../standard-library/exception-functions.md#set_unexpected).

Program obsługi nieoczekiwanych wyjątków nie może zwrócić do obiektu wywołującego. Go może zakończyć wykonywania przez:

- Zwracając obiekt typu wymienionego w specyfikacji wyjątku lub obiekt dowolnego typu, jeśli program obsługi nieoczekiwanych wyjątków jest wywoływany bezpośrednio przez program.

- Zgłaszanie obiektu typu [bad_exception](../standard-library/bad-exception-class.md).

- Wywoływanie [zakończyć](../standard-library/exception-functions.md#terminate), `abort` lub **wyjść**(`int`).

W momencie uruchamiania programu, program obsługi nieoczekiwanych wyjątków jest funkcją, która wywołuje [zakończyć](../standard-library/exception-functions.md#terminate).

### <a name="example"></a>Przykład

Zobacz [set_unexpected](../standard-library/exception-functions.md#set_unexpected) przykładem użycia `unexpected`.

## <a name="see-also"></a>Zobacz także

[\<wyjątku >](../standard-library/exception.md)<br/>

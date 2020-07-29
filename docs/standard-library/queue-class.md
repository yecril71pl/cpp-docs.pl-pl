---
title: queue — Klasa
ms.date: 11/04/2016
f1_keywords:
- queue/std::queue::container_type
- queue/std::queue::size_type
- queue/std::queue::value_type
- queue/std::queue::back
- queue/std::queue::empty
- queue/std::queue::front
- queue/std::queue::pop
- queue/std::queue::push
- queue/std::queue::size
helpviewer_keywords:
- std::queue [C++], container_type
- std::queue [C++], size_type
- std::queue [C++], value_type
- std::queue [C++], back
- std::queue [C++], empty
- std::queue [C++], front
- std::queue [C++], pop
- std::queue [C++], push
- std::queue [C++], size
ms.assetid: 28c20ab0-3a72-4185-9e0f-5a44eea0e204
ms.openlocfilehash: 331ca298507e0ebecac0376f660feefdafd9d99d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232940"
---
# <a name="queue-class"></a>queue — Klasa

Klasa adaptera kontenerów szablonu, która zapewnia ograniczenie funkcjonalności dla pewnego typu kontenera, ograniczając dostęp do elementów przednich i tylnych. Elementy mogą być dodawane z tyłu lub usuwane z przodu, a elementy można sprawdzić na końcu kolejki.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>Parametry

*Wprowadź*\
Typ danych elementu, który ma być przechowywany w kolejce

*Wbudowane*\
Typ źródłowego kontenera używany do implementowania kolejki.

## <a name="remarks"></a>Uwagi

Elementy klasy `Type` ustalone w pierwszym parametrze szablonu obiektu kolejki są synonimem [value_type](#value_type) i muszą być zgodne z typem elementu w klasie bazowego kontenera `Container` określonym przez drugi parametr szablonu. `Type`Należy je przypisać, aby można było kopiować obiekty tego typu i przypisywać wartości do zmiennych tego typu.

Odpowiednie źródłowe klasy kontenerów dla kolejki obejmują [deque](../standard-library/deque-class.md) i [listę](../standard-library/list-class.md)oraz każdy inny kontener sekwencji obsługujący operacje `front` , `back` , `push_back` , i `pop_front` . Bazowa Klasa kontenera jest hermetyzowana w ramach adaptera kontenerów, która uwidacznia tylko ograniczony zestaw funkcji Członkowskich kontenera sekwencji jako interfejs publiczny.

Obiekty kolejek są równe porównywalnie, jeśli i tylko wtedy, gdy elementy klasy `Type` mają porównywalne równość i są mniejsze niż porównywalne, jeśli elementy klasy `Type` są mniejsze niż porównywalne.

Istnieją trzy typy adapterów kontenerów zdefiniowane przez standardową bibliotekę języka C++: Stack, Queue i priority_queue. Każdy z nich ogranicza funkcjonalność pewnej klasy bazowego kontenera do zapewnienia precyzyjnego kontrolowanego interfejsu do standardowej struktury danych.

- [Klasa stosu](../standard-library/stack-class.md) obsługuje strukturę danych Last-in, First-Out (LIFO). Dobrym sposobem na zachowywać się to stos płyt. Elementy (płytki) mogą być wstawiane, badane lub usuwane tylko z góry stosu, który jest ostatnim elementem na końcu kontenera podstawowego. Ograniczenie dostępu do elementu Top jest przyczyną użycia klasy stosu.

- Klasa Queue obsługuje strukturę danych First-In, First-Out (FIFO). Dobrym analogem na to, aby mieć na uwadze, osoby tworzące informację o poinformowaniu banku. Elementy (ludzie) mogą zostać dodane z tyłu wiersza i są usuwane z przodu wiersza. Można sprawdzić zarówno przód, jak i tyłu wiersza. Ograniczenie do uzyskiwania dostępu tylko do elementów przednich i z tyłu w ten sposób jest przyczyną użycia klasy kolejki.

- [Klasa priority_queue](../standard-library/priority-queue-class.md) porządkuje swoje elementy, aby największy element zawsze znajduje się na górze. Obsługuje wstawianie elementu i inspekcję oraz usuwanie elementu Top. Dobrym analogicznym sposobem jest pogrupowanie osób, które są ułożone według wieku, wysokości lub innego kryterium.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[niej](#queue)|Tworzy element a `queue` , który jest pusty lub jest kopią podstawowego obiektu kontenera.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[container_type](#container_type)|Typ, który dostarcza kontener podstawowy, który ma zostać dostosowany przez `queue` .|
|[size_type](#size_type)|Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w `queue` .|
|[value_type](#value_type)|Typ, który reprezentuje typ obiektu przechowywanego jako element w `queue` .|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[Wstecz](#back)|Zwraca odwołanie do ostatniego i ostatnio dodanego elementu z tyłu `queue` .|
|[puste](#empty)|Testuje, czy `queue` jest pusty.|
|[FSB](#front)|Zwraca odwołanie do pierwszego elementu z przodu `queue` .|
|[skakując](#pop)|Usuwa element z przodu `queue` .|
|[push](#push)|Dodaje element do tyłu `queue` .|
|[zmienia](#size)|Zwraca liczbę elementów w `queue` .|

## <a name="back"></a><a name="back"></a>Wstecz

Zwraca odwołanie do ostatniego i ostatnio dodanego elementu z tyłu kolejki.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Ostatni element kolejki. Jeśli kolejka jest pusta, wartość zwracana jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `back` jest przypisana do `const_reference` , nie można zmodyfikować obiektu kolejki. Jeśli wartość zwracana `back` jest przypisana do `reference` , obiekt kolejki może być modyfikowany.

Podczas kompilowania przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowanego jako 1 lub 2, wystąpi błąd czasu wykonywania, jeśli spróbujesz uzyskać dostęp do elementu w pustej kolejce.  Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Przykład

```cpp
// queue_back.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 11 );

   int& i = q1.back( );
   const int& ii = q1.front( );

   cout << "The integer at the back of queue q1 is " << i
        << "." << endl;
   cout << "The integer at the front of queue q1 is " << ii
        << "." << endl;
}
```

## <a name="container_type"></a><a name="container_type"></a>container_type

Typ, który dostarcza kontener bazowy, który ma zostać dostosowany.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Container` . Dwie klasy kontenerów sekwencji standardowej biblioteki języka C++ — Klasa listy i domyślna klasa deque — spełniają wymagania, które mają być używane jako kontener podstawowy dla obiektu kolejki. Typy zdefiniowane przez użytkownika spełniające wymagania mogą być również używane.

Aby uzyskać więcej informacji na temat `Container` , zobacz sekcję Uwagi w temacie [Klasa kolejki](../standard-library/queue-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [kolejki](#queue) , aby zapoznać się z przykładem sposobu deklarowania i używania `container_type` .

## <a name="empty"></a><a name="empty"></a>ciągiem

Testuje, czy kolejka jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli kolejka jest pusta; **`false`** Jeśli kolejka nie jest pusta.

### <a name="example"></a>Przykład

```cpp
// queue_empty.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2;

   q1.push( 1 );

   if ( q1.empty( ) )
      cout << "The queue q1 is empty." << endl;
   else
      cout << "The queue q1 is not empty." << endl;

   if ( q2.empty( ) )
      cout << "The queue q2 is empty." << endl;
   else
      cout << "The queue q2 is not empty." << endl;
}
```

```Output
The queue q1 is not empty.
The queue q2 is empty.
```

## <a name="front"></a><a name="front"></a>FSB

Zwraca odwołanie do pierwszego elementu na początku kolejki.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy element kolejki. Jeśli kolejka jest pusta, wartość zwracana jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `front` jest przypisana do `const_reference` , nie można zmodyfikować obiektu kolejki. Jeśli wartość zwracana `front` jest przypisana do `reference` , obiekt kolejki może być modyfikowany.

Funkcja członkowska zwraca `reference` do pierwszego elementu kontrolowanej sekwencji, która nie może być pusta.

Podczas kompilowania przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowanego jako 1 lub 2, wystąpi błąd czasu wykonywania, jeśli spróbujesz uzyskać dostęp do elementu w pustej kolejce.  Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Przykład

```cpp
// queue_front.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main() {
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   int& ii = q1.back( );
   int& iii = q1.front( );

   cout << "The integer at the back of queue q1 is " << ii
        << "." << endl;
   cout << "The integer at the front of queue q1 is " << iii
        << "." << endl;
}
```

## <a name="pop"></a><a name="pop"></a>skakując

Usuwa element z przodu kolejki.

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Kolejka musi być niepusta, aby można było zastosować funkcję członkowską. Góra kolejki jest pozycją zajmowaną przez ostatnio dodany element i jest ostatnim elementem na końcu kontenera.

### <a name="example"></a>Przykład

```cpp
// queue_pop.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, s2;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   i = q1.front( );
   cout << "The element at the front of the queue is "
        << i << "." << endl;

   q1.pop( );

   i = q1.size( );
   cout << "After a pop the queue length is "
        << i << "." << endl;

   i = q1. front ( );
   cout << "After a pop, the element at the front of the queue is "
        << i << "." << endl;
}
```

```Output
The queue length is 3.
The element at the front of the queue is 10.
After a pop the queue length is 2.
After a pop, the element at the front of the queue is 20.
```

## <a name="push"></a><a name="push"></a>wydajności

Dodaje element do tyłu kolejki.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*użyte*\
Element dodany do tyłu kolejki.

### <a name="remarks"></a>Uwagi

Tyłu kolejki jest pozycja zajmowana przez ostatnio dodany element i jest ostatnim elementem na końcu kontenera.

### <a name="example"></a>Przykład

```cpp
// queue_push.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   i = q1.front( );
   cout << "The element at the front of the queue is "
        << i << "." << endl;
}
```

```Output
The queue length is 3.
The element at the front of the queue is 10.
```

## <a name="queue"></a><a name="queue"></a>niej

Tworzy kolejkę, która jest pusta lub jest kopią podstawowego obiektu kontenera.

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Kontener, w **`const`** którym skonstruowana kolejka ma być kopią.

### <a name="remarks"></a>Uwagi

Domyślny kontener bazowy dla kolejki to deque. Można również określić listę jako kontener podstawowy, ale nie można określić wektora, ponieważ brakuje wymaganej `pop_front` funkcji składowej.

### <a name="example"></a>Przykład

```cpp
// queue_queue.cpp
// compile with: /EHsc
#include <queue>
#include <vector>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queue with default deque base container
   queue <char> q1;

   // Explicitly declares a queue with deque base container
   queue <char, deque<char> > q2;

   // These lines don't cause an error, even though they
   // declares a queue with a vector base container
   queue <int, vector<int> > q3;
   q3.push( 10 );
   // but the following would cause an error because vector has
   // no pop_front member function
   // q3.pop( );

   // Declares a queue with list base container
   queue <int, list<int> > q4;

   // The second member function copies elements from a container
   list<int> li1;
   li1.push_back( 1 );
   li1.push_back( 2 );
   queue <int, list<int> > q5( li1 );
   cout << "The element at the front of queue q5 is "
        << q5.front( ) << "." << endl;
   cout << "The element at the back of queue q5 is "
        << q5.back( ) << "." << endl;
}
```

```Output
The element at the front of queue q5 is 1.
The element at the back of queue q5 is 2.
```

## <a name="size"></a><a name="size"></a>zmienia

Zwraca liczbę elementów w kolejce.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość kolejki.

### <a name="example"></a>Przykład

```cpp
// queue_size.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2;
   queue <int>::size_type i;

   q1.push( 1 );
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   q1.push( 2 );
   i = q1.size( );
   cout << "The queue length is now " << i << "." << endl;
}
```

```Output
The queue length is 1.
The queue length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a>size_type

Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w kolejce.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `size_type` kontenera podstawowego dostosowany przez kolejkę.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [kolejki:: front](#front) , aby zapoznać się z przykładem sposobu deklarowania i używania `size_type` .

## <a name="value_type"></a><a name="value_type"></a>value_type

Typ, który reprezentuje typ obiektu przechowywanego jako element w kolejce.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `value_type` kontenera podstawowego dostosowany przez kolejkę.

### <a name="example"></a>Przykład

```cpp
// queue_value_type.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
using namespace std;

   // Declares queues with default deque base container
   queue<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   queue<int> q1;
   q1.push(AnInt);
   cout << "The element at the front of the queue is "
        << q1.front( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the front of the queue is 69.
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)

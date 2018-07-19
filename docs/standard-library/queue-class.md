---
title: Queue — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d50b53f9c06c5edbd159e7e2bac112f6f30432df
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954919"
---
# <a name="queue-class"></a>queue — Klasa

Klasa adaptera kontenera szablonu, która umożliwia ograniczenie funkcjonalności dla pewnego bazowego typu kontenera, ograniczanie dostępu do elementów w przód i Wstecz. Elementy, które mogą być dodane w tle lub wiodących, a elementy mogą być kontrolowane na końcu kolejki.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>Parametry

*Typ* typ danych elementu mają być przechowywane w kolejce

*Kontener* typu bazowego kontenera, używaną do zaimplementowania kolejki.

## <a name="remarks"></a>Uwagi

Elementy klasy `Type` określone w szablonie pierwszy parametr obiekt kolejki jest równoznaczny z [value_type](#value_type) i musi odpowiadać typowi elementu w klasie podstawowej kontenera `Container` określonymi przez drugi parametr szablonu. `Type` Musi być możliwy do przypisania, więc jest możliwe, aby skopiować obiekty tego typu, a także do przypisywania wartości do zmiennych tego typu.

Dołączyć odpowiednie podstawowej klasy kontenera dla kolejki [deque](../standard-library/deque-class.md) i [listy](../standard-library/list-class.md), lub innego kontenera sekwencji, która obsługuje operacje `front`, `back`, `push_back`, i `pop_front`. Podstawowej klasy kontenera są hermetyzowane w obrębie adaptera kontenera, który uwidacznia tylko ograniczony zestaw funkcji elementów członkowskich kontenerów sekwencji jako interfejs publiczny.

Kolejki obiekty są wtedy porównywanie równości i tylko wtedy, gdy elementy klasy `Type` są porównywalne równości i mniej-niż porównywalne wtedy i tylko wtedy, gdy elementy klasy `Type` są mniejsze-niż porównywalne.

Istnieją trzy typy adaptery kontenera definicją standardowej biblioteki języka C++: stosu, kolejki i priority_queue —. Każdy ogranicza funkcjonalność niektóre podstawowe klasy kontenera dokładnie kontrolowanym interfejs do struktury danych w warstwie standardowa.

- [Stack — klasa](../standard-library/stack-class.md) obsługuje ostatni na wejściu, first-out (LIFO) strukturę danych. Dobre analogowy na uwadze byłoby były stosem talerzy. Elementy (talerzy) może wstawiania, inspekcji lub usunąć tylko z góry stosu, w którym jest ostatnim elementem na końcu podstawowym kontenerem. Ograniczenie do uzyskiwania dostępu do górnego elementu jest przyczyna przy użyciu klasy stosu.

- Klasa kolejki obsługuje pierwszy in, first-out (FIFO) strukturę danych. Dobre analogowy na uwadze byłoby osób wyrównywania dla dla kasjerów bankowych. Elementy (osób) mogą być dodawane do końca wiersza i są usuwane z początku wiersza. Mogą być kontrolowane zarówno do przodu, jak i do tyłu wiersza. Ograniczenie do uzyskiwania dostępu do tylko przód i Wstecz elementy w ten sposób jest przyczyna przy użyciu klasy kolejki.

- [Priority_queue — klasa](../standard-library/priority-queue-class.md) porządkuje jego elementy, dzięki czemu największy element jest zawsze u góry. Obsługuje ona Wstawianie elementu i inspekcji i usuwania górnego elementu. Dobre analogowy na uwadze byłoby osób wyrównywanie gdzie one są uporządkowane według wiek, wysokości lub innego kryterium.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[kolejki](#queue)|Konstruuje `queue` pusty lub jest kopię obiektu podstawowego kontenera.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który zapewnia podstawowy kontener, aby zostać dostosowane przez `queue`.|
|[size_type](#size_type)|Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w `queue`.|
|[value_type](#value_type)|Typ, który reprezentuje typ obiektu przechowywanego jako element w `queue`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[back](#back)|Zwraca odwołanie do ostatniego i ostatnio dodane elementu na tworzenie kopii zapasowych `queue`.|
|[pusty](#empty)|Sprawdza, czy `queue` jest pusty.|
|[Frontonu](#front)|Zwraca odwołanie do pierwszego elementu na początku `queue`.|
|[POP](#pop)|Usuwa element z przodu `queue`.|
|[push](#push)|Dodaje element do tyłu `queue`.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `queue`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<kolejki >

**Namespace:** standardowe

## <a name="back"></a>  Queue::back

Zwraca odwołanie do ostatniego i ostatnio dodane element tyłu kolejki.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Ostatni element kolejki. Jeśli kolejka jest pusta, zwracana wartość jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `back` jest przypisany do `const_reference`, nie można zmodyfikować obiektu kolejki. Jeśli wartość zwracaną przez `back` jest przypisany do `reference`, można zmodyfikować obiekt kolejki.

Gdy kompilowany przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowana jako 1 lub 2, wystąpi błąd czasu wykonywania przy próbie uzyskania dostępu do elementu w pustej kolejce.  Zobacz [Checked Iterators](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

## <a name="container_type"></a>  Queue::container_type

Typ, który dostarcza podstawowy kontener, aby dostosować.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Container`. Dwie klasy kontenera sekwencja standardowej biblioteki języka C++ — klasa listy i domyślną klasę deque — spełniają wymagania, które ma być używany jako bazowy kontener dla obiektu kolejki. Typy zdefiniowane przez użytkownika niespełniających wymagań można także.

Aby uzyskać więcej informacji na temat `Container`, zobacz sekcję Uwagi [kolejkowania klasy](../standard-library/queue-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [kolejki](#queue) przykładowy sposób deklarowania i użyj `container_type`.

## <a name="empty"></a>  Queue::Empty

Sprawdza, czy kolejka jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli kolejka jest pusta. **false** Jeśli kolejka jest niepusty.

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

## <a name="front"></a>  Queue::front

Zwraca odwołanie do pierwszego elementu na wierzchu kolejki.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy element w kolejce. Jeśli kolejka jest pusta, zwracana wartość jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracaną przez `front` jest przypisany do `const_reference`, nie można zmodyfikować obiektu kolejki. Jeśli wartość zwracaną przez `front` jest przypisany do `reference`, można zmodyfikować obiekt kolejki.

Funkcja elementu członkowskiego zwraca `reference` do pierwszego elementu w kontrolowanej sekwencji, która nie może być puste.

Gdy kompilowany przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowana jako 1 lub 2, wystąpi błąd czasu wykonywania przy próbie uzyskania dostępu do elementu w pustej kolejce.  Zobacz [Checked Iterators](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

## <a name="pop"></a>  Queue::POP

Usuwa element z przodu kolejki.

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Kolejka nie może być puste do zastosowania funkcji elementu członkowskiego. Początku kolejki jest pozycja zajmowane przez element ostatnio dodane i ostatni element na końcu kontenera.

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

## <a name="push"></a>  Queue::push

Dodaje element do tyłu kolejki.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val* elementu dodany do tyłu kolejki.

### <a name="remarks"></a>Uwagi

Wstecz kolejki jest pozycja zajmowane przez element ostatnio dodane i ostatni element na końcu kontenera.

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

## <a name="queue"></a>  Queue::Queue

Tworzy kolejki, który jest pusty lub jest kopią obiektu podstawowego kontenera.

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>Parametry

*prawy* **const** kontenera, w której skonstruowany kolejki jest kopią.

### <a name="remarks"></a>Uwagi

Domyślny kontener podstawowy dla kolejki jest deque. Można również określić listy jako podstawowy kontener, ale nie można określić wektora, ponieważ brakuje wymaganych `pop_front` funkcja elementu członkowskiego.

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

## <a name="size"></a>  Queue::size

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

## <a name="size_type"></a>  Queue::size_type

Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w kolejce.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `size_type` podstawowy kontenera dostosowane przez kolejkę.

### <a name="example"></a>Przykład

Zobacz przykład [queue::front](#front) przykładowy sposób deklarowania i użyj `size_type`.

## <a name="value_type"></a>  Queue::value_type

Typ, który reprezentuje typ obiektu przechowywanego jako element w kolejce.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `value_type` podstawowy kontenera dostosowane przez kolejkę.

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

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>

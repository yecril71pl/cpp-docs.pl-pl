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
ms.openlocfilehash: 5442888e8e370892add687c21132e397ae683ac8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="queue-class"></a>queue — Klasa

Klasa karty kontenera szablonu, która umożliwia ograniczenie funkcjonalności dla niektórych odpowiedni typ kontenera, ograniczanie dostępu do elementów front i back. Elementy można dodać na tylnej lub wiodących i elementy mogą być kontrolowane na końcu kolejki.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>Parametry

*Typ* typu danych elementu mają być przechowywane w kolejce

`Container` Typ podstawowy kontenera używaną do zaimplementowania kolejki.

## <a name="remarks"></a>Uwagi

Elementy klasy **typu** określone w szablonie pierwszy parametr obiekt kolejki jest tożsame z [value_type](#value_type) i musi odpowiadać typowi element w klasie podstawowej kontenera **Kontenera** określone przez drugi parametr szablonu. **Typu** musi być możliwa do przypisania, dzięki czemu możliwe jest do kopii obiektów tego typu i można przypisać wartości do zmiennych typu.

Obejmują odpowiedniej klasy kontenerów podstawowej dla kolejki [deque —](../standard-library/deque-class.md) i [listy](../standard-library/list-class.md), lub inne kontenera sekwencji, która obsługuje operacje `front`, **ponownie** , `push_back`, i `pop_front`. Podstawowe klasy kontenera jest hermetyzowany w ramach karty kontenera, który udostępnia tylko ograniczony zestaw funkcji Członkowskich sekwencji kontener jako publiczny interfejs.

Kolejki obiektów, to jeśli można porównywać pod względem równości i tylko wtedy, gdy elementy klasy **typu** są można porównywać pod względem równości i mniejsze-niż porównywalne w przypadku i tylko wtedy, gdy elementy klasy **typu** są mniejsze-niż porównywanie.

Istnieją trzy typy adapterów kontenera zdefiniowane przez standardowa biblioteka C++: stosu, kolejki i priority_queue —. Każdy ogranicza funkcjonalność niektórych podstawowych klasy kontenera dokładnie kontrolowanym interfejs do struktury danych standardowych.

- [Stack — klasa](../standard-library/stack-class.md) obsługuje ostatni na, wytworzenia struktura danych. Dobrym analogowy należy wziąć pod uwagę będzie stosu tablic. Elementy (płyty) może wstawiania, inspekcji lub usunąć tylko z góry stosu, w którym jest ostatni element w końcu podstawowej kontenera. Ograniczenie do uzyskiwania dostępu do górnego elementu jest przyczyna za pomocą klasy stosu.

- Klasa kolejki obsługuje pierwszy w, FIFO (FIFO) struktury danych. Dobrym analogowy należy wziąć pod uwagę będzie Wyrównywanie dla kasjerów bankowych osób. Elementy (użytkownicy) mogą być dodawane do tyłu wiersza i są usuwane z na początku wiersza. Może być sprawdzany przodu i z powrotem wiersza. Ograniczenie do uzyskiwania dostępu do tylko front i back elementów w ten sposób jest przyczyna za pomocą klasy kolejki.

- [Priority_queue — klasa](../standard-library/priority-queue-class.md) porządkuje swoich elementów, aby największy element zawsze znajduje się w górnej pozycji. Obsługuje ona wstawiania elementu oraz inspekcji i usuwaniu górnego elementu. Dobrym analogowy należy wziąć pod uwagę będzie osób wyrównywanie, gdzie są uporządkowane według ważności, wysokość lub innego kryterium.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Kolejki](#queue)|Konstruuje `queue` pusta lub jest kopię obiektu podstawowego kontenera.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który zapewnia podstawową kontener należy dostosować przez `queue`.|
|[size_type](#size_type)|Typu Liczba całkowita bez znaku, który może reprezentować liczbę elementów w `queue`.|
|[value_type](#value_type)|Typ, który reprezentuje typ obiektu przechowywane jako elementu `queue`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[back](#back)|Zwraca odwołanie do ostatniego i ostatnio dodany element na tworzenie kopii `queue`.|
|[pusty](#empty)|Sprawdza, czy `queue` jest pusta.|
|[Front](#front)|Zwraca odwołanie do pierwszego elementu z przodu `queue`.|
|[POP](#pop)|Usuwa element z przodu `queue`.|
|[push](#push)|Dodaje element do tyłu `queue`.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `queue`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<kolejki >

**Namespace:** Standard

## <a name="back"></a>  Queue::back

Zwraca odwołanie do ostatniego i ostatnio dodane element w końcu kolejki.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Ostatnim elementem kolejki. Jeśli kolejka jest pusta, zwracana wartość jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana **ponownie** jest przypisany do `const_reference`, obiekt kolejki nie może być modyfikowany. Jeśli wartość zwracana **ponownie** jest przypisany do **odwołania**, obiekt kolejki może być modyfikowany.

Podczas kompilacji za pomocą [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowany jako 1 lub 2, błąd środowiska uruchomieniowego nastąpi próba uzyskania dostępu do elementu w pustej kolejce.  Zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

Typ, który zapewnia podstawową kontener dostosowania.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu `Container`. Klasy kontenerów w dwóch sekwencji standardowa biblioteka C++ — klasa listy i domyślne deque — klasa — spełniać wymagania dotyczące służyć jako podstawowa kontener dla obiekt kolejki. Typy danych zdefiniowane przez użytkownika spełnia wymagania mogą również.

Aby uzyskać więcej informacji na temat `Container`, zobacz sekcję uwag [kolejka klasy](../standard-library/queue-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [kolejki](#queue) przykład sposobu deklarowanie i użycie `container_type`.

## <a name="empty"></a>  Queue::Empty

Testy, jeśli kolejka jest pusta.

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

Zwraca odwołanie do pierwszego elementu z przodu kolejki.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy element kolejki. Jeśli kolejka jest pusta, zwracana wartość jest niezdefiniowana.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana `front` jest przypisany do `const_reference`, obiekt kolejki nie może być modyfikowany. Jeśli wartość zwracana `front` jest przypisany do **odwołania**, obiekt kolejki może być modyfikowany.

Funkcja członkowska zwraca **odwołania** do pierwszego elementu w kontrolowanej sekwencji, która nie może być puste.

Podczas kompilacji za pomocą [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowany jako 1 lub 2, błąd środowiska uruchomieniowego nastąpi próba uzyskania dostępu do elementu w pustej kolejce.  Zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

Kolejki nie może być puste, aby zastosować funkcji członkowskiej. Na początku kolejki jest zajmowane przez element ostatnio dodane stanowisko i ostatni element w końcu kontenera.

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

`val` Element dodany do tyłu kolejki.

### <a name="remarks"></a>Uwagi

Wstecz kolejki jest zajmowane przez element ostatnio dodane stanowisko i ostatni element w końcu kontenera.

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

Tworzy kolejka jest pusta lub kopię obiektu podstawowego kontenera.

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>Parametry

`right` **Const** kontenera skonstruowane kolejki ma być kopii.

### <a name="remarks"></a>Uwagi

Domyślny kontener podstawowy dla kolejki jest deque —. Listy można również określić jako kontener podstawowy, ale nie można określić wektora, ponieważ nie ma wymaganego `pop_front` funkcję elementu członkowskiego.

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

Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w kolejce.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `size_type` podstawowej kontenera dostosowane przez kolejkę.

### <a name="example"></a>Przykład

Zobacz przykład [queue::front](#front) przykład sposobu deklarowanie i użycie `size_type`.

## <a name="value_type"></a>  Queue::value_type

Typ, który reprezentuje typ obiektu przechowywane jako element w kolejce.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `value_type` podstawowej kontenera dostosowane przez kolejkę.

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

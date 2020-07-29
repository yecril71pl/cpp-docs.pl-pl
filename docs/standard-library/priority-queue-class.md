---
title: priority_queue — Klasa
ms.date: 11/04/2016
f1_keywords:
- queue/std::priority_queue::container_type
- queue/std::priority_queue::size_type
- queue/std::priority_queue::value_type
- queue/std::priority_queue::empty
- queue/std::priority_queue::pop
- queue/std::priority_queue::push
- queue/std::priority_queue::size
- queue/std::priority_queue::top
helpviewer_keywords:
- std::priority_queue [C++], container_type
- std::priority_queue [C++], size_type
- std::priority_queue [C++], value_type
- std::priority_queue [C++], empty
- std::priority_queue [C++], pop
- std::priority_queue [C++], push
- std::priority_queue [C++], size
- std::priority_queue [C++], top
ms.assetid: 69fca9cc-a449-4be4-97b7-02ca5db9cbb2
ms.openlocfilehash: 8a1b33e45d066082a0f225067db84a6240e8fc53
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232953"
---
# <a name="priority_queue-class"></a>priority_queue — Klasa

Klasa adaptera kontenerów szablonu, która zapewnia ograniczenie funkcjonalności ograniczające dostęp do górnego elementu pewnego bazowego typu kontenera, który jest zawsze największy lub najwyższy priorytet. Nowe elementy można dodać do priority_queue, a górny element priority_queue można sprawdzić lub usunąć.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>Parametry

*Wprowadź*\
Typ danych elementu, który ma być przechowywany w priority_queue.

*Wbudowane*\
Typ źródłowego kontenera używany do implementowania priority_queue.

*Porównaniu*\
Typ, który dostarcza obiekt funkcji, który może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w priority_queue. Ten argument jest opcjonalny, a Predykat binarny `less<typename Container::value_type>` jest wartością domyślną.

## <a name="remarks"></a>Uwagi

Elementy klasy `Type` ustalone w pierwszym parametrze szablonu obiektu kolejki są synonimem [value_type](#value_type) i muszą być zgodne z typem elementu w klasie bazowego kontenera `Container` określonym przez drugi parametr szablonu. `Type`Należy je przypisać, aby można było kopiować obiekty tego typu i przypisywać wartości do zmiennych tego typu.

Priority_queue porządkuje sekwencję, która kontroluje, wywołując obiekt funkcji składowanej klasy `Traits` . Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym.

Odpowiednie źródłowe klasy kontenerów dla priority_queue obejmują [klasę deque](../standard-library/deque-class.md) oraz domyślną [klasę wektorów](../standard-library/vector-class.md) lub inny kontener sekwencji obsługujący operacje `front` , `push_back` i `pop_back` i Iterator dostępu swobodnego. Bazowa Klasa kontenera jest hermetyzowana w ramach adaptera kontenerów, która uwidacznia tylko ograniczony zestaw funkcji Członkowskich kontenera sekwencji jako interfejs publiczny.

Dodawanie elementów do i usuwanie elementów z obu tych wartości `priority_queue` ma złożoność logarytmiczną. Uzyskiwanie dostępu do elementów w programie `priority_queue` ma stałą złożoność.

Istnieją trzy typy adapterów kontenerów zdefiniowane przez standardową bibliotekę języka C++: Stack, Queue i priority_queue. Każdy z nich ogranicza funkcjonalność pewnej klasy bazowego kontenera do zapewnienia precyzyjnego kontrolowanego interfejsu do standardowej struktury danych.

- [Klasa stosu](../standard-library/stack-class.md) obsługuje strukturę danych Last-in, First-Out (LIFO). Dobrym sposobem na zachowywać się to stos płyt. Elementy (płytki) mogą być wstawiane, badane lub usuwane tylko z góry stosu, który jest ostatnim elementem na końcu kontenera podstawowego. Ograniczenie dostępu do elementu Top jest przyczyną użycia klasy stosu.

- [Klasa Queue](../standard-library/queue-class.md) obsługuje strukturę danych First-In, First-Out (FIFO). Dobrym analogem na to, aby mieć na uwadze, osoby tworzące informację o poinformowaniu banku. Elementy (ludzie) mogą zostać dodane z tyłu wiersza i są usuwane z przodu wiersza. Można sprawdzić zarówno przód, jak i tyłu wiersza. Ograniczenie do uzyskiwania dostępu tylko do elementów przednich i z tyłu w ten sposób jest przyczyną użycia klasy kolejki.

- Klasa priority_queue porządkuje swoje elementy, aby największy element zawsze znajduje się na górze. Obsługuje wstawianie elementu i inspekcję oraz usuwanie elementu Top. Dobrym analogicznym sposobem jest pogrupowanie osób, które są ułożone według wieku, wysokości lub innego kryterium.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[priority_queue](#priority_queue)|Tworzy element a `priority_queue` , który jest pusty lub jest kopią zakresu podstawowego obiektu kontenera lub innych `priority_queue` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który dostarcza kontener podstawowy, który ma zostać dostosowany przez `priority_queue` .|
|[size_type](#size_type)|Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w `priority_queue` .|
|[value_type](#value_type)|Typ, który reprezentuje typ obiektu przechowywanego jako element w `priority_queue` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[puste](#empty)|Testuje, czy `priority_queue` jest pusty.|
|[skakując](#pop)|Usuwa największy element z `priority_queue` powyższego położenia.|
|[push](#push)|Dodaje element do kolejki priorytetu na podstawie priorytetu elementu z< operatora.|
|[zmienia](#size)|Zwraca liczbę elementów w `priority_queue` .|
|[top (pierwsze)](#top)|Zwraca odwołanie const do największego elementu w górnej części `priority_queue` .|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<queue>

**Przestrzeń nazw:** std

## <a name="priority_queuecontainer_type"></a><a name="container_type"></a>priority_queue:: container_type

Typ, który dostarcza kontener bazowy, który ma zostać dostosowany.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Container` . Klasa kontenera sekwencji standardowej biblioteki C++ `deque` i Klasa domyślna `vector` spełniają wymagania, które mają być używane jako kontener podstawowy dla obiektu priority_queue. Typy zdefiniowane przez użytkownika spełniające wymagania mogą być również używane.

Aby uzyskać więcej informacji na temat `Container` , zobacz sekcję Uwagi w temacie [priority_queue Class](../standard-library/priority-queue-class.md) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [priority_queue](#priority_queue) , aby zapoznać się z przykładem sposobu deklarowania i używania `container_type` .

## <a name="priority_queueempty"></a><a name="empty"></a>priority_queue:: Empty

Testuje, czy priority_queue jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli priority_queue jest puste; **`false`** jeśli priority_queue nie jest pusty.

### <a name="example"></a>Przykład

```cpp
// pqueue_empty.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares priority_queues with default deque base container
   priority_queue <int> q1, s2;

   q1.push( 1 );

   if ( q1.empty( ) )
      cout << "The priority_queue q1 is empty." << endl;
   else
      cout << "The priority_queue q1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The priority_queue s2 is empty." << endl;
   else
      cout << "The priority_queue s2 is not empty." << endl;
}
```

```Output
The priority_queue q1 is not empty.
The priority_queue s2 is empty.
```

## <a name="priority_queuepop"></a><a name="pop"></a>priority_queue::p op

Usuwa największy element priority_queue z pozycji najwyższego poziomu.

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Priority_queue nie może być pusta, aby zastosować funkcję członkowską. Górna część priority_queue jest zawsze zajęta przez największy element w kontenerze.

### <a name="example"></a>Przykład

```cpp
// pqueue_pop.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue <int> q1, s2;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   priority_queue <int>::size_type i, iii;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;

   q1.pop( );

   iii = q1.size( );
   cout << "After a pop, the priority_queue length is "
        << iii << "." << endl;

   const int& iv = q1.top( );
   cout << "After a pop, the element at the top of the "
        << "priority_queue is " << iv << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
After a pop, the priority_queue length is 2.
After a pop, the element at the top of the priority_queue is 20.
```

## <a name="priority_queuepriority_queue"></a><a name="priority_queue"></a>priority_queue::p riority_queue

Konstruuje priority_queue, który jest pusty lub jest kopią zakresu podstawowego obiektu kontenera lub innego priority_queue.

```cpp
priority_queue();

explicit priority_queue(const Traits& _comp);

priority_queue(const Traits& _comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits& _comp);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits& _comp, const container_type& _Cont);
```

### <a name="parameters"></a>Parametry

*_comp*\
Funkcja porównania typu **constTraits** użyta do uporządkowania elementów w priority_queue, które domyślnie porównują funkcję w kontenerze podstawowym.

*_Cont*\
Podstawowy kontener, którego skonstruowany priority_queue ma być kopią.

*Kliknij*\
Priority_queue, do którego skonstruowany jest zestaw, to kopia.

*pierwszego*\
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*ostatniego*\
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

Każdy z trzech pierwszych konstruktorów określa pustą priority_queue początkową, drugi także określa typ funkcji porównywania ( `comp` ), która ma być używana w celu ustalenia kolejności elementów i trzeciego jawnie określającego `container_type` (), `_Cont` który ma być używany. Słowo kluczowe **`explicit`** pomija pewne rodzaje automatycznej konwersji typów.

Czwarty Konstruktor określa kopię priority_queue *prawej*.

Ostatnie trzy konstruktory skopiują zakres \[ *pierwszy*, *ostatni*) z pewnego kontenera i używają wartości, aby zainicjować priority_queue, zwiększając jawność w określaniu typu funkcji porównania klasy `Traits` i `container_type` .

### <a name="example"></a>Przykład

```cpp
// pqueue_ctor.cpp
// compile with: /EHsc
#include <queue>
#include <vector>
#include <deque>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function declares priority_queue
   // with a default vector base container
   priority_queue <int> q1;
   cout << "q1 = ( ";
   while ( !q1.empty( ) )
   {
      cout << q1.top( ) << " ";
      q1.pop( );
   }
   cout << ")" << endl;

   // Explicitly declares a priority_queue with nondefault
   // deque base container
   priority_queue <int, deque <int> > q2;
   q2.push( 5 );
   q2.push( 15 );
   q2.push( 10 );
   cout << "q2 = ( ";
   while ( !q2.empty( ) )
   {
      cout << q2.top( ) << " ";
      q2.pop( );
   }
   cout << ")" << endl;

   // This method of printing out the elements of a priority_queue
   // removes the elements from the priority queue, leaving it empty
   cout << "After printing, q2 has " << q2.size( ) << " elements." << endl;

   // The third member function declares a priority_queue
   // with a vector base container and specifies that the comparison
   // function greater is to be used for ordering elements
   priority_queue <int, vector<int>, greater<int> > q3;
   q3.push( 2 );
   q3.push( 1 );
   q3.push( 3 );
   cout << "q3 = ( ";
   while ( !q3.empty( ) )
   {
      cout << q3.top( ) << " ";
      q3.pop( );
   }
   cout << ")" << endl;

   // The fourth member function declares a priority_queue and
   // initializes it with elements copied from another container:
   // first, inserting elements into q1, then copying q1 elements into q4
   q1.push( 100 );
   q1.push( 200 );
   priority_queue <int> q4( q1 );
   cout << "q4 = ( ";
   while ( !q4.empty( ) )
   {
      cout << q4.top( ) << " ";
      q4.pop( );
   }
   cout << ")" << endl;

   // Creates an auxiliary vector object v5 to be used to initialize q5
   vector <int> v5;
   vector <int>::iterator v5_Iter;
   v5.push_back( 10 );
   v5.push_back( 30 );
   v5.push_back( 20 );
   cout << "v5 = ( " ;
   for ( v5_Iter = v5.begin( ) ; v5_Iter != v5.end( ) ; v5_Iter++ )
      cout << *v5_Iter << " ";
   cout << ")" << endl;

   // The fifth member function declares and
   // initializes a priority_queue q5 by copying the
   // range v5[ first,  last) from vector v5
   priority_queue <int> q5( v5.begin( ), v5.begin( ) + 2 );
   cout << "q5 = ( ";
   while ( !q5.empty( ) )
   {
      cout << q5.top( ) << " ";
      q5.pop( );
   }
   cout << ")" << endl;

   // The sixth member function declares a priority_queue q6
   // with a comparison function greater and initializes q6
   // by copying the range v5[ first,  last) from vector v5
   priority_queue <int, vector<int>, greater<int> >
      q6( v5.begin( ), v5.begin( ) + 2 );
   cout << "q6 = ( ";
   while ( !q6.empty( ) )
   {
      cout << q6.top( ) << " ";
      q6.pop( );
   }
   cout << ")" << endl;
}
```

## <a name="priority_queuepush"></a><a name="push"></a>priority_queue::p USH

Dodaje element do kolejki priorytetu na podstawie priorytetu elementu z< operatora.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*użyte*\
Element dodany na górze priority_queue.

### <a name="remarks"></a>Uwagi

Górna część priority_queue to pozycja zajmowana przez największy element w kontenerze.

### <a name="example"></a>Przykład

```cpp
// pqueue_push.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue<int> q1;

   q1.push( 10 );
   q1.push( 30 );
   q1.push( 20 );

   priority_queue<int>::size_type i;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
```

## <a name="priority_queuesize"></a><a name="size"></a>priority_queue:: size

Zwraca liczbę elementów w priority_queue.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość priority_queue.

### <a name="example"></a>Przykład

```cpp
// pqueue_size.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue <int> q1, q2;
   priority_queue <int>::size_type i;

   q1.push( 1 );
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   q1.push( 2 );
   i = q1.size( );
   cout << "The priority_queue length is now " << i << "." << endl;
}
```

```Output
The priority_queue length is 1.
The priority_queue length is now 2.
```

## <a name="priority_queuesize_type"></a><a name="size_type"></a>priority_queue:: size_type

Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w priority_queue.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `size_type` kontenera podstawowego dostosowany przez priority_queue.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dotyczącym [rozmiaru](#size) , aby zapoznać się z przykładem sposobu deklarowania i używania `size_type` .

## <a name="priority_queuetop"></a><a name="top"></a>priority_queue:: Top

Zwraca odwołanie const do największego elementu w górnej części priority_queue.

```cpp
const_reference top() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do największego elementu, określonego przez `Traits` funkcję, obiektu priority_queue.

### <a name="remarks"></a>Uwagi

Priority_queue nie może być pusta, aby zastosować funkcję członkowską.

### <a name="example"></a>Przykład

```cpp
// pqueue_top.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue<int> q1;

   q1.push( 10 );
   q1.push( 30 );
   q1.push( 20 );

   priority_queue<int>::size_type i;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
```

## <a name="priority_queuevalue_type"></a><a name="value_type"></a>priority_queue:: value_type

Typ, który reprezentuje typ obiektu przechowywanego jako element w priority_queue.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `value_type` kontenera podstawowego dostosowany przez priority_queue.

### <a name="example"></a>Przykład

```cpp
// pqueue_value_type.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares priority_queues with default deque base container
   priority_queue<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   priority_queue<int> q1;
   q1.push( AnInt );
   cout << "The element at the top of the priority_queue is "
        << q1.top( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the top of the priority_queue is 69.
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)

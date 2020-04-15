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
ms.openlocfilehash: cef85eafaa3aab1c448234399f146191de957b8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323012"
---
# <a name="priority_queue-class"></a>priority_queue — Klasa

Klasa adaptera kontenera szablonu, która zapewnia ograniczenie funkcjonalności ograniczające dostęp do górnego elementu jakiegoś typu kontenera źródłowego, który jest zawsze największy lub o najwyższym priorytecie. Nowe elementy mogą być dodawane do priority_queue a górny element priority_queue może być kontrolowane lub usuwane.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>Parametry

*Typu*\
Typ danych elementu, który ma być przechowywany w priority_queue.

*Kontenera*\
Typ kontenera źródłowego używanego do implementowania priority_queue.

*Porównać*\
Typ, który udostępnia obiekt funkcji, który może porównać dwie wartości elementu jako klucze sortowania w celu określenia ich względnej kolejności w priority_queue. Ten argument jest opcjonalny, `less<typename Container::value_type>` a predykat binarny jest wartością domyślną.

## <a name="remarks"></a>Uwagi

Elementy klasy `Type` określone w pierwszym parametrze szablonu obiektu kolejki są synonimem [value_type](#value_type) i muszą być zgodne z `Container` typem elementu w podstawowej klasy kontenera określone przez drugi parametr szablonu. Musi `Type` być przypisany, tak aby można było kopiować obiekty tego typu i przypisywać wartości do zmiennych tego typu.

Priority_queue porządkuuje sekwencję, która kontroluje, wywołując przechowywany `Traits`obiekt funkcji klasy . Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym.

Odpowiednie klasy kontenerów bazowych dla priority_queue obejmują [klasę deque](../standard-library/deque-class.md) i [domyślną klasę wektorową](../standard-library/vector-class.md) lub inny kontener sekwencji, który obsługuje operacje `front`, `push_back`i `pop_back` iterator dostępu losowego. Podstawowa klasa kontenera jest hermetyzowany w ramach adaptera kontenera, który udostępnia tylko ograniczony zestaw elementów członkowskich kontenera sekwencji działa jako interfejs publiczny.

Dodawanie elementów i usuwanie `priority_queue` elementów z obu mają złożoność logarytmicznej. Dostęp do elementów w ma stałą `priority_queue` złożoność.

Istnieją trzy typy adapterów kontenerów zdefiniowane przez standardową bibliotekę języka C++: stos, kolejka i priority_queue. Każdy ogranicza funkcjonalność niektórych klasy kontenera podstawowej, aby zapewnić precyzyjnie kontrolowany interfejs do standardowej struktury danych.

- Klasa [stosu](../standard-library/stack-class.md) obsługuje strukturę danych last-in, first-out (LIFO). Dobrym analogiem, o który należy pamiętać, byłby stos płyt. Elementy (płyty) mogą być wstawiane, kontrolowane lub usuwane tylko z górnej części stosu, który jest ostatnim elementem na końcu pojemnika bazowego. Ograniczenie dostępu tylko do górnego elementu jest przyczyną używania stack klasy.

- Klasa [kolejki](../standard-library/queue-class.md) obsługuje strukturę danych FIFO (first-in, first-out). Dobrym analogiem, o który należy pamiętać, będą ludzie ustawiający się w kolejce do kasjera bankowego. Elementy (osoby) mogą być dodawane do tylnej części linii i usuwane z przodu linii. Zarówno przód, jak i tył linii mogą być kontrolowane. Ograniczenie dostępu tylko do elementów z przodu i z tyłu w ten sposób jest powodem używania klasy kolejki.

- Klasa priority_queue porządkuji swoje elementy, tak aby największy element jest zawsze na najwyższym położeniu. Obsługuje wstawienie elementu oraz kontrolę i usuwanie górnego elementu. Dobrym analogiem, o którym należy pamiętać, będą ludzie ustawiający się w kolejce tam, gdzie są ułożone według wieku, wzrostu lub innego kryterium.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Priority_queue](#priority_queue)|Konstruuje `priority_queue` pustą lub kopię zakresu obiektu kontenera podstawowego lub `priority_queue`innego .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który zapewnia podstawowy pojemnik, który `priority_queue`ma być dostosowany przez .|
|[size_type](#size_type)|Niepodpisany typ liczby całkowitej, który może `priority_queue`reprezentować liczbę elementów w programie .|
|[value_type](#value_type)|Typ reprezentujący typ obiektu przechowywanego jako `priority_queue`element w pliku .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Pusty](#empty)|Sprawdza, `priority_queue` czy jest pusty.|
|[Pop](#pop)|Usuwa największy element `priority_queue` z górnej pozycji.|
|[Push](#push)|Dodaje element do kolejki priorytetu na podstawie priorytetu elementu z< operatora.|
|[Rozmiar](#size)|Zwraca liczbę elementów `priority_queue`w pliku .|
|[Do góry](#top)|Zwraca odwołanie const do największego elementu `priority_queue`w górnej części .|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> kolejki

**Przestrzeń nazw:** std

## <a name="priority_queuecontainer_type"></a><a name="container_type"></a>priority_queue::container_type

Typ, który zapewnia podstawowy kontener, który ma zostać dostosowany.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `Container`szablonu . Klasa `deque` kontenera sekwencji biblioteki standardowej `vector` języka C++ i klasa domyślna spełniają wymagania, które mają być używane jako kontener podstawowy dla obiektu priority_queue. Można również stosować typy zdefiniowane przez użytkownika spełniające wymagania.

Aby uzyskać `Container`więcej informacji na temat , zobacz uwagi sekcji [priority_queue class](../standard-library/priority-queue-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [priority_queue](#priority_queue) na przykład jak zadeklarować i `container_type`używać .

## <a name="priority_queueempty"></a><a name="empty"></a>priority_queue::empty

Sprawdza, czy priority_queue jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli priority_queue jest pusta; **false,** jeśli priority_queue jest niepusty.

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

## <a name="priority_queuepop"></a><a name="pop"></a>priority_queue::pop

Usuwa największy element priority_queue z górnej pozycji.

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Priority_queue musi być niepusty, aby zastosować funkcję elementu członkowskiego. Górna część priority_queue jest zawsze zajmowana przez największy element w kontenerze.

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

## <a name="priority_queuepriority_queue"></a><a name="priority_queue"></a>priority_queue::priority_queue

Tworzy priority_queue, który jest pusty lub jest kopią zakresu obiektu kontenera podstawowego lub innego priority_queue.

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
Funkcja porównania typu **constTraits** używane do zamawiania elementów w priority_queue, który domyślnie do porównania funkcji kontenera podstawowego.

*_Cont*\
Podstawowy kontener, którego priority_queue skonstruowane ma być kopią.

*Prawo*\
priority_queue którego konstruowany zestaw ma być kopią.

*Pierwszym*\
Położenie pierwszego elementu w zakresie elementów do skopiowania.

*Ostatnio*\
Położenie pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

Każdy z pierwszych trzech konstruktorów określa pusty początkowy priority_queue, drugi określa również`comp`typ funkcji porównania ( ) do użycia przy ustalaniu `container_type` `_Cont`kolejności elementów, a trzeci wyraźnie określając ( ) do użycia. Słowo kluczowe **jawne** pomija niektóre rodzaje konwersji typu automatycznego.

Czwarty konstruktor określa kopię priority_queue *prawej*.

Trzy ostatnie konstruktory \[kopiują zakres *pierwszy,* *ostatni*) niektórych kontenerów i używają wartości do inicjowania `Traits` `container_type`priority_queue z rosnącą jawnością w określaniu typu funkcji porównania klasy i .

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

## <a name="priority_queuepush"></a><a name="push"></a>priority_queue::push

Dodaje element do kolejki priorytetu na podstawie priorytetu elementu z< operatora.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Element dodany do górnej części priority_queue.

### <a name="remarks"></a>Uwagi

Górna część priority_queue jest pozycją zajmowaną przez największy element w kontenerze.

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

## <a name="priority_queuesize"></a><a name="size"></a>priority_queue::size

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

## <a name="priority_queuesize_type"></a><a name="size_type"></a>priority_queue::size_type

Niepodpisany typ liczby całkowitej, który może reprezentować liczbę elementów w priority_queue.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `size_type` kontenera podstawowego dostosowanego przez priority_queue.

### <a name="example"></a>Przykład

Zobacz przykład [rozmiaru,](#size) aby uzyskać przykład sposobu `size_type`deklarowania i używania .

## <a name="priority_queuetop"></a><a name="top"></a>priority_queue::góra

Zwraca odwołanie const do największego elementu w górnej części priority_queue.

```cpp
const_reference top() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do największego elementu, zgodnie `Traits` z funkcją, obiekt priority_queue.

### <a name="remarks"></a>Uwagi

Priority_queue musi być niepusty, aby zastosować funkcję elementu członkowskiego.

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

## <a name="priority_queuevalue_type"></a><a name="value_type"></a>priority_queue::value_type

Typ, który reprezentuje typ obiektu przechowywanego jako element w priority_queue.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `value_type` kontenera podstawowego dostosowanego przez priority_queue.

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

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)

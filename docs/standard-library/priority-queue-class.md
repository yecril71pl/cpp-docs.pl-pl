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
ms.openlocfilehash: d8f2b4ab788c82e531d1121f04dd0d422efb17cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370019"
---
# <a name="priorityqueue-class"></a>priority_queue — Klasa

Klasa adaptera kontenera szablonu, która umożliwia ograniczenie funkcjonalności, ograniczanie dostępu do górnego elementu niektóre bazowego typu kontenera, który zawsze jest największy, lub o najwyższym priorytecie. Nowe elementy mogą być dodawane do priority_queue — i górnego elementu priority_queue — mogą być kontrolowane lub usunięta.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Typ danych elementu, który ma być przechowywany w priority_queue —.

*Kontener*<br/>
Typ podstawowy kontener używany do implementowania priority_queue —.

*Compare*<br/>
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w priority_queue —. Ten argument jest opcjonalny i predykat dwuelementowy `less<typename Container::value_type>` jest wartością domyślną.

## <a name="remarks"></a>Uwagi

Elementy klasy `Type` określone w szablonie pierwszy parametr obiekt kolejki jest równoznaczny z [value_type](#value_type) i musi odpowiadać typowi elementu w klasie podstawowej kontenera `Container` określonymi przez drugi parametr szablonu. `Type` Musi być możliwy do przypisania, więc jest możliwe, aby skopiować obiekty tego typu, a także do przypisywania wartości do zmiennych tego typu.

Priority_queue — porządkuje sekwencję którą kontroluje, przez wywołanie przechowywanego obiektu funkcji klasy `Traits`. Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym.

Odpowiednie podstawowej klasy kontenera dla priority_queue — obejmują [deque — klasa](../standard-library/deque-class.md) i domyślnego [vector, klasa](../standard-library/vector-class.md) lub innego kontenera sekwencji, która obsługuje operacje `front`, `push_back`, i `pop_back` i iterator dostępu swobodnego. Podstawowej klasy kontenera są hermetyzowane w obrębie adaptera kontenera, który uwidacznia tylko ograniczony zestaw funkcji elementów członkowskich kontenerów sekwencji jako interfejs publiczny.

Dodawanie elementów do i usuwanie elementów z `priority_queue` mają logarytmicznej złożoności. Uzyskiwanie dostępu do elementów w `priority_queue` ma stałą złożoność.

Istnieją trzy typy adaptery kontenera definicją C++ standardowej biblioteki: stosu, kolejki i priority_queue —. Każdy ogranicza funkcjonalność niektóre podstawowe klasy kontenera dokładnie kontrolowanym interfejs do struktury danych w warstwie standardowa.

- [Stack — klasa](../standard-library/stack-class.md) obsługuje ostatni na wejściu, first-out (LIFO) strukturę danych. Dobre analogowy na uwadze byłoby były stosem talerzy. Elementy (talerzy) może wstawiania, inspekcji lub usunąć tylko z góry stosu, w którym jest ostatnim elementem na końcu podstawowym kontenerem. Ograniczenie do uzyskiwania dostępu do górnego elementu jest przyczyna przy użyciu klasy stosu.

- [Kolejkowania klasy](../standard-library/queue-class.md) obsługuje pierwszy in, first-out (FIFO) strukturę danych. Dobre analogowy na uwadze byłoby osób wyrównywania dla dla kasjerów bankowych. Elementy (osób) mogą być dodawane do końca wiersza i są usuwane z początku wiersza. Mogą być kontrolowane zarówno do przodu, jak i do tyłu wiersza. Ograniczenie do uzyskiwania dostępu do tylko przód i Wstecz elementy w ten sposób jest przyczyna przy użyciu klasy kolejki.

- Priority_queue — klasa zamówień jego elementy, dzięki czemu największy element jest zawsze u góry. Obsługuje ona Wstawianie elementu i inspekcji i usuwania górnego elementu. Dobre analogowy na uwadze byłoby osób wyrównywanie gdzie one są uporządkowane według wiek, wysokości lub innego kryterium.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[priority_queue](#priority_queue)|Konstruuje `priority_queue` pusty lub jest kopii zakresu obiektu kontenera podstawowej lub innych `priority_queue`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który zapewnia podstawowy kontener, aby zostać dostosowane przez `priority_queue`.|
|[size_type](#size_type)|Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w `priority_queue`.|
|[value_type](#value_type)|Typ, który reprezentuje typ obiektu przechowywanego jako element w `priority_queue`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[pusty](#empty)|Sprawdza, czy `priority_queue` jest pusty.|
|[POP](#pop)|Usuwa największy element z `priority_queue` z góry.|
|[push](#push)|Dodaje element do kolejki priorytetowej na podstawie priorytetu elementu od operatora <.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `priority_queue`.|
|[Do góry](#top)|Zwraca wartość typu const odwołanie do największego elementu w górnej części `priority_queue`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<kolejki >

**Namespace:** standardowe

## <a name="container_type"></a>  priority_queue::container_type

Typ, który dostarcza podstawowy kontener, aby dostosować.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Container`. C++ Klasy kontenera sekwencja standardowej biblioteki `deque` i domyślną klasę `vector` spełniają wymagania, które ma być używany jako bazowy kontener dla obiektu priority_queue —. Typy zdefiniowane przez użytkownika niespełniających wymagań można także.

Aby uzyskać więcej informacji na temat `Container`, zobacz sekcję Uwagi [priority_queue — klasa](../standard-library/priority-queue-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [priority_queue —](#priority_queue) przykładowy sposób deklarowania i użyj `container_type`.

## <a name="empty"></a>  priority_queue::Empty

Sprawdza, czy priority_queue — jest pusty.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli priority_queue — jest pusta. **false** przypadku niepustych priority_queue —.

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

## <a name="pop"></a>  priority_queue::POP

Usuwa największy element priority_queue — z góry.

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Priority_queue — musi być niepustym do zastosowania funkcji elementu członkowskiego. Priority_queue — początku zawsze jest zajęta przez największego elementu w kontenerze.

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

## <a name="priority_queue"></a>  priority_queue::priority_queue

Tworzy priority_queue —, który jest pusty lub jest kopią zakresu obiektu kontenera podstawowego lub innego priority_queue —.

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

*_comp*<br/>
Funkcja porównywania typu **constTraits** porządkowania elementów w priority_queue — wartość domyślna to porównanie funkcji podstawowym kontenerem.

*_Cont*<br/>
Podstawowy kontener, którego skonstruowany priority_queue — jest kopią.

*right*<br/>
Priority_queue — której zestaw zbudowany jest kopią.

*pierwszy*<br/>
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*last*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

Każdy pierwsze trzy konstruktory Określa pusty początkowej priority_queue —, drugi również określenie typu funkcji porównywania (`comp`) do użycia podczas ustalania kolejności elementów, a trzeci jawnie określając `container_type`(`_Cont`) ma być używany. Słowo kluczowe **jawne** powoduje pominięcie niektórych rodzajów konwersji typu automatyczne.

Czwarty Konstruktor Określa kopię priority_queue — *prawo*.

Ostatnie trzy konstruktory kopiują zakres \[ *pierwszy*, *ostatniego*) niektóre kontenera i użyć wartości, aby zainicjować priority_queue — uwzględni się rosnącą explicitness podczas określania typu Porównanie funkcji klasy `Traits` i `container_type`.

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

## <a name="push"></a>  priority_queue::push

Dodaje element do kolejki priorytetowej na podstawie priorytetu elementu od operatora <.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Element dodany na początku priority_queue —.

### <a name="remarks"></a>Uwagi

Górnej priority_queue — jest pozycja zajmowane przez największego elementu w kontenerze.

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

## <a name="size"></a>  priority_queue::size

Priority_queue — zwraca liczbę elementów.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca długość priority_queue —.

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

## <a name="size_type"></a>  priority_queue::size_type

Typ całkowitoliczbowy bez znaku, który może reprezentować liczbę elementów w priority_queue —.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `size_type` podstawowy kontenera dostosowane przez priority_queue —.

### <a name="example"></a>Przykład

Zobacz przykład [rozmiar](#size) przykładowy sposób deklarowania i użyj `size_type`.

## <a name="top"></a>  priority_queue::Top

Zwraca wartość const odwołanie do największego elementu w górnej części priority_queue —.

```cpp
const_reference top() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do największego elementu zgodnie z ustaleniami `Traits` funkcji, obiekt priority_queue —.

### <a name="remarks"></a>Uwagi

Priority_queue — musi być niepustym do zastosowania funkcji elementu członkowskiego.

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

## <a name="value_type"></a>  priority_queue::value_type

Typ, który reprezentuje typ obiektu przechowywanego jako element w priority_queue —.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `value_type` podstawowy kontenera dostosowane przez priority_queue —.

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

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>

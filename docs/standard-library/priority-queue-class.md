---
title: priority_queue — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- queue/std::priority_queue::container_type
- queue/std::priority_queue::size_type
- queue/std::priority_queue::value_type
- queue/std::priority_queue::empty
- queue/std::priority_queue::pop
- queue/std::priority_queue::push
- queue/std::priority_queue::size
- queue/std::priority_queue::top
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 149d255dd82d0dff2d2ddb1101b38bf05c69673a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861919"
---
# <a name="priorityqueue-class"></a>priority_queue — Klasa

Klasa karty kontenera szablonu, która umożliwia ograniczenie funkcjonalności ograniczanie dostępu do elementu górnego niektórych odpowiedni typ kontenera, która jest zawsze największej lub o najwyższym priorytecie. Nowe elementy mogą zostać dodane do priority_queue — i górnego elementu priority_queue — mogą być kontrolowane lub usunięty.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>Parametry

*Typ* mają być przechowywane w priority_queue — typ danych elementu.

`Container` Typ podstawowy kontenera używaną do zaimplementowania priority_queue —.

*Porównaj* typu, która zawiera obiekt funkcji, które można porównać dwóch wartości elementu jako klucze sortowania, aby określić ich kolejność względne w priority_queue —. Ten argument jest opcjonalny i binarne predykatu **mniej***\<*** typename** *kontenera ***:: value_type*** >* jest wartością domyślną.

## <a name="remarks"></a>Uwagi

Elementy klasy **typu** określone w szablonie pierwszy parametr obiekt kolejki jest tożsame z [value_type](#value_type) i musi odpowiadać typowi element w klasie podstawowej kontenera **Kontenera** określone przez drugi parametr szablonu. **Typu** musi być możliwa do przypisania, dzięki czemu możliwe jest do kopii obiektów tego typu i można przypisać wartości do zmiennych typu.

Priority_queue — porządkuje sekwencji kontroluje przez wywołanie obiektu przechowywanej funkcji klasy **cech**. Ogólnie rzecz biorąc, elementy muszą być nieco mniej porównywalne, aby ustalić kolejność: tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi) lub, że jeden jest mniejszy niż ten drugi. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Ze strony bardziej technicznej, funkcja porównywania jest predykatem binarnym, który wymusza ścisłe słabe porządkowanie w standardowym sensie matematycznym.

Dołączyć odpowiednie podstawowej klasy kontener dla priority_queue — [deque — klasa](../standard-library/deque-class.md) i domyślnie [vector — klasa](../standard-library/vector-class.md) lub innych kontenera sekwencji, która obsługuje operacje `front`, `push_back`, i `pop_back` i iterator dostępie swobodnym. Podstawowe klasy kontenera jest hermetyzowany w ramach karty kontenera, który udostępnia tylko ograniczony zestaw funkcji Członkowskich sekwencji kontener jako publiczny interfejs.

Dodawanie elementów i usuwanie elementów z `priority_queue` mają logarytmicznej złożoności. Uzyskiwanie dostępu do elementów w `priority_queue` ma stałą złożoności.

Istnieją trzy typy adapterów kontenera zdefiniowane przez standardowa biblioteka C++: stosu, kolejki i priority_queue —. Każdy ogranicza funkcjonalność niektórych podstawowych klasy kontenera dokładnie kontrolowanym interfejs do struktury danych standardowych.

- [Stack — klasa](../standard-library/stack-class.md) obsługuje ostatni na, wytworzenia struktura danych. Dobrym analogowy należy wziąć pod uwagę będzie stosu tablic. Elementy (płyty) może wstawiania, inspekcji lub usunąć tylko z góry stosu, w którym jest ostatni element w końcu podstawowej kontenera. Ograniczenie do uzyskiwania dostępu do górnego elementu jest przyczyna za pomocą klasy stosu.

- [Kolejka klasy](../standard-library/queue-class.md) obsługuje pierwszy w, FIFO (FIFO) struktury danych. Dobrym analogowy należy wziąć pod uwagę będzie Wyrównywanie dla kasjerów bankowych osób. Elementy (użytkownicy) mogą być dodawane do tyłu wiersza i są usuwane z na początku wiersza. Może być sprawdzany przodu i z powrotem wiersza. Ograniczenie do uzyskiwania dostępu do tylko front i back elementów w ten sposób jest przyczyna za pomocą klasy kolejki.

- Priority_queue — klasa zamówień swoich elementów, aby największy element zawsze znajduje się w górnej pozycji. Obsługuje ona wstawiania elementu oraz inspekcji i usuwaniu górnego elementu. Dobrym analogowy należy wziąć pod uwagę będzie osób wyrównywanie, gdzie są uporządkowane według ważności, wysokość lub innego kryterium.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[priority_queue](#priority_queue)|Konstruuje `priority_queue` pusta lub jest kopię zakresu obiektu kontenera podstawowej lub innych `priority_queue`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który zapewnia podstawową kontener należy dostosować przez `priority_queue`.|
|[size_type](#size_type)|Typu Liczba całkowita bez znaku, który może reprezentować liczbę elementów w `priority_queue`.|
|[value_type](#value_type)|Typ, który reprezentuje typ obiektu przechowywane jako elementu `priority_queue`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[pusty](#empty)|Sprawdza, czy `priority_queue` jest pusta.|
|[POP](#pop)|Usuwa element największą `priority_queue` z górnej pozycji.|
|[push](#push)|Dodaje element do kolejki priorytetu na podstawie priorytetu elementu od operatora <.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `priority_queue`.|
|[Do góry](#top)|Zwraca wartość typu const odwołanie do największy element na początku `priority_queue`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<kolejki >

**Namespace:** Standard

## <a name="container_type"></a>  priority_queue::container_type

Typ, który zapewnia podstawową kontener dostosowania.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu `Container`. Klasa standardowa biblioteka C++ sekwencji `deque` i domyślną klasę `vector` spełniać wymagania dotyczące służyć jako podstawowa kontener dla obiekt priority_queue —. Typy danych zdefiniowane przez użytkownika spełnia wymagania mogą również.

Aby uzyskać więcej informacji na temat `Container`, zobacz sekcję uwag [priority_queue — klasa](../standard-library/priority-queue-class.md) tematu.

### <a name="example"></a>Przykład

Zobacz przykład [priority_queue —](#priority_queue) przykład sposobu deklarowanie i użycie `container_type`.

## <a name="empty"></a>  priority_queue::Empty

Testy, jeśli priority_queue — jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli priority_queue — jest pusta. **false** Jeśli priority_queue — nie jest pusty.

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

Usuwa największy element priority_queue — z górnej pozycji.

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Priority_queue — nie może być puste, aby zastosować funkcję elementu członkowskiego. Na początku priority_queue — zawsze jest zajęte przez element największy w kontenerze.

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

Tworzy priority_queue —, który jest pusta lub który jest kopią zakresu obiektu kontenera podstawowej lub innego priority_queue —.

```cpp
priority_queue();

explicit priority_queue(const Traits&_comp);

priority_queue(const Traits&_comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits&_comp);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits&_comp, const container_type& _Cont);
```

### <a name="parameters"></a>Parametry

*kompozycja _* Funkcja porównywania typu **constTraits** porządkowania elementów w priority_queue — domyślnie porównanie funkcji podstawowej kontenera.

`_Cont` Kontener podstawowej skonstruowane priority_queue — ma być kopii.

`right` Priority_queue — skonstruowane zestawu ma być kopii.

`first` Pozycja pierwszego elementu w zakresie elementów do skopiowania.

`last` Pozycja pierwszego elementu poza zakres elementów do skopiowania.

### <a name="remarks"></a>Uwagi

Określa każdego z trzech pierwszych konstruktorów pusty początkowej priority_queue —, druga również określenie typu porównanie funkcji ( `comp`) do użycia w ustalaniu kolejności elementów i trzeci jawnie określając `container_type`( `_Cont`) do użycia. Słowo kluczowe **jawne** pomija określonych rodzajów typu automatycznej konwersji.

Konstruktor czwarty Określa kopię priority_queue — `right`.

Ostatnie trzy konstruktorów skopiuj zakres [* pierwszy, ostatni *) niektórych kontenera i użyj wartości, aby zainicjować priority_queue — rosnącymi explicitness określania typu porównanie funkcji klasy **cech** i `container_type`.

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

Dodaje element do kolejki priorytetu na podstawie priorytetu elementu od operatora <.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

`val` Element dodany do góry priority_queue —.

### <a name="remarks"></a>Uwagi

Na początku priority_queue — to pozycja zajmowane przez największy element w kontenerze.

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

Zwraca liczbę elementów w priority_queue —.

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

Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów w priority_queue —.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `size_type` podstawowej kontenera dostosowane przez priority_queue —.

### <a name="example"></a>Przykład

Zobacz przykład [rozmiar](#size) przykład sposobu deklarowanie i użycie `size_type`.

## <a name="top"></a>  priority_queue::Top

Zwraca const odwołanie do największy element w górnej części priority_queue —.

```cpp
const_reference top() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu największy, zgodnie z ustaleniami **cech** funkcji, obiekt priority_queue —.

### <a name="remarks"></a>Uwagi

Priority_queue — nie może być puste, aby zastosować funkcję elementu członkowskiego.

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

Typ, który reprezentuje typ obiektu przechowywane jako element priority_queue —.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `value_type` podstawowej kontenera dostosowane przez priority_queue —.

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

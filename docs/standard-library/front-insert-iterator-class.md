---
title: front_insert_iterator — Klasa
ms.date: 11/04/2016
f1_keywords:
- iterator/std::front_insert_iterator
- iterator/std::front_insert_iterator::container_type
- iterator/std::front_insert_iterator::reference
helpviewer_keywords:
- std::front_insert_iterator [C++]
- std::front_insert_iterator [C++], container_type
- std::front_insert_iterator [C++], reference
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
ms.openlocfilehash: 8f60b2e5e21b559edb630be2aee377341d4480f6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203276"
---
# <a name="front_insert_iterator-class"></a>front_insert_iterator — Klasa

Opisuje adapter iteratora, który spełnia wymagania iteratora danych wyjściowych. Wstawia (a nie zastępuje) elementy do przedniego końca sekwencji i w ten sposób zapewnia semantykę, która różni się od semantyki zastępowania, dostarczanej przez iteratory kontenerów sekwencji C++. `front_insert_iterator`Klasa jest szablonowana w typie kontenera.

## <a name="syntax"></a>Składnia

```cpp
template <class Container>
class front_insert_iterator;
```

### <a name="parameters"></a>Parametry

*Wbudowane*\
Typ kontenera na początku elementów, które mają zostać wstawione przez `front_insert_iterator` .

## <a name="remarks"></a>Uwagi

Kontener musi spełniać wymagania dla sekwencji wstawiania na przód, gdzie jest możliwe wstawianie elementów na początek sekwencji w amortyzowanym stałym czasie. Kontenery sekwencji standardowej biblioteki C++ zdefiniowane przez [klasę deque](../standard-library/deque-class.md) i [klasę listy](../standard-library/list-class.md) zapewniają potrzebną `push_front` funkcję członkowską i spełniają te wymagania. Z kolei Kontenery sekwencji zdefiniowane przez [klasę Vector](../standard-library/vector-class.md) nie spełniają tych wymagań i nie można ich dostosować do użycia z atrybutami `front_insert_iterator` s. Element A `front_insert_iterator` musi zawsze być zainicjowany przy użyciu jego kontenera.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[front_insert_iterator](#front_insert_iterator)|Tworzy iterator, który może wstawić elementy z przodu określonego obiektu kontenera.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który reprezentuje kontener, w którym ma być przeprowadzone wstawienie na przód.|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[zakład](#op_star)|Operator dereferencji używany do implementowania wyrażenia iteratora danych wyjściowych \* `i`  =  `x` dla wstawiania z przodu.|
|[operator + +](#op_add_add)|Zwiększa `front_insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.|
|[operator =](#op_eq)|Operator przypisania używany do implementowania wyrażenia iteratora danych wyjściowych \* `i`  =  `x` dla wstawiania z przodu.|

## <a name="requirements"></a>Wymagania

**Nagłówek**:\<iterator>

**Przestrzeń nazw:** std

## <a name="front_insert_iteratorcontainer_type"></a><a name="container_type"></a>front_insert_iterator:: container_type

Typ, który reprezentuje kontener, w którym ma być przeprowadzone wstawienie na przód.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla *kontenera*parametrów szablonu.

### <a name="example"></a>Przykład

```cpp
// front_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> >::container_type L2 = L1;
   front_inserter ( L2 ) = 20;
   front_inserter ( L2 ) = 10;
   front_inserter ( L2 ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 10 20 ).
*/
```

## <a name="front_insert_iteratorfront_insert_iterator"></a><a name="front_insert_iterator"></a>front_insert_iterator:: front_insert_iterator

Tworzy iterator, który może wstawić elementy z przodu określonego obiektu kontenera.

```cpp
explicit front_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Obiekt kontenera, do którego `front_insert_iterator` ma zostać wstawiony element.

### <a name="return-value"></a>Wartość zwracana

A `front_insert_iterator` dla obiektu kontenera parametrów.

### <a name="example"></a>Przykład

```cpp
// front_insert_iterator_front_insert_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   front_inserter ( L ) = 20;

   // Alternatively, one may use the template function
   front_insert_iterator< list < int> > Iter(L);
*Iter = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_star"></a>front_insert_iterator:: operator\*

Usuwa odwołanie do iteratora INSERT zwracające element, który zawiera.

```cpp
front_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca wartość elementu, do którego się odnosi.

### <a name="remarks"></a>Uwagi

Służy do implementowania wyrażenia iteratora danych wyjściowych ** \* ITER**  =  **value**. Jeśli `Iter` jest iteratorem, który dotyczy elementu w sekwencji, a następnie ** \* ITER**  =  **wartość** zastępuje ten element wartością i nie zmienia łącznej liczby elementów w sekwencji.

### <a name="example"></a>Przykład

```cpp
// front_insert_iterator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   front_insert_iterator< list < int> > Iter(L);
*Iter = 20;

   // Alternatively, you may use
   front_inserter ( L ) = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_add_add"></a>front_insert_iterator:: operator + +

Zwiększa `back_insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.

```cpp
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

`front_insert_iterator`Adresowanie następnej lokalizacji, w której może być przechowywana wartość.

### <a name="remarks"></a>Uwagi

Operatory przedrastające i postincrementation zwracają ten sam wynik.

### <a name="example"></a>Przykład

```cpp
// front_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_eq"></a>front_insert_iterator:: operator =

Dołącza (wypchnięcia) wartość na wierzchu kontenera.

```cpp
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

*użyte*\
Wartość, która ma zostać przypisana do kontenera.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ostatniego elementu wstawionego na początku kontenera.

### <a name="remarks"></a>Uwagi

Pierwszy operator elementu członkowskiego oblicza `container.push_front( val)` , a następnie zwraca **`*this`** .

Drugi operator elementu członkowskiego oblicza

`container->push_front((typename Container::value_type&&) val)`,

następnie zwraca wartość **`*this`** .

### <a name="example"></a>Przykład

```cpp
// front_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="front_insert_iteratorreference"></a><a name="reference"></a>front_insert_iterator:: Reference

Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.

```cpp
typedef typename Container::reference reference;
```

### <a name="example"></a>Przykład

```cpp
// front_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   front_insert_iterator<list<int> > fiivIter( L );
*fiivIter = 10;
*fiivIter = 20;
*fiivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++)
      cout << *LIter << " ";
   cout << ")." << endl;

   front_insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 30 20 10 ).
The first element in the list L is: 30.
*/
```

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)

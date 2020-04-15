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
ms.openlocfilehash: 455db433aff1c1aa241beeb6e2435807959b7dd4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317151"
---
# <a name="front_insert_iterator-class"></a>front_insert_iterator — Klasa

Opisuje adapter iteratora, który spełnia wymagania iteratora danych wyjściowych. Wstawia (a nie zastępuje) elementy do przedniego końca sekwencji i w ten sposób zapewnia semantykę, która różni się od semantyki zastępowania, dostarczanej przez iteratory kontenerów sekwencji C++. Klasa `front_insert_iterator` jest templatized na typ kontenera.

## <a name="syntax"></a>Składnia

```cpp
template <class Container>
class front_insert_iterator;
```

### <a name="parameters"></a>Parametry

*Kontenera*\
Typ pojemnika z przodu, którego elementy mają być `front_insert_iterator`wstawione przez .

## <a name="remarks"></a>Uwagi

Kontener musi spełniać wymagania dla sekwencji wstawiania na przód, gdzie jest możliwe wstawianie elementów na początek sekwencji w amortyzowanym stałym czasie. Kontenery sekwencji biblioteki standardowej języka C++ zdefiniowane `push_front` przez klasę [deque i](../standard-library/deque-class.md) [list](../standard-library/list-class.md) zapewniają wymagani funkcję elementu członkowskiego i spełniają te wymagania. Natomiast kontenery sekwencji zdefiniowane przez [klasę wektorową](../standard-library/vector-class.md) nie spełniają tych wymagań `front_insert_iterator`i nie mogą być dostosowane do użycia z s. A `front_insert_iterator` musi być zawsze zainicjowany za pomocą jego kontenera.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[front_insert_iterator](#front_insert_iterator)|Tworzy iterator, który może wstawić elementy z przodu określonego obiektu kontenera.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który reprezentuje kontener, w którym ma być przeprowadzone wstawienie na przód.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator*](#op_star)|Dereferencing operator używany do implementacji \* `i`  =  `x` wyrażenia iteratora wyjściowego dla wstawiania z przodu.|
|[operator++](#op_add_add)|Zwiększa do `front_insert_iterator` następnej lokalizacji, w której wartość może być przechowywana.|
|[operator=](#op_eq)|Operator przypisania używany do implementacji \* `i`  =  `x` wyrażenia iteratora wyjściowego dla wstawiania z przodu.|

## <a name="requirements"></a>Wymagania

**Nagłówek** \<:> iteratora

**Przestrzeń nazw:** std

## <a name="front_insert_iteratorcontainer_type"></a><a name="container_type"></a>front_insert_iterator::container_type

Typ, który reprezentuje kontener, w którym ma być przeprowadzone wstawienie na przód.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru *szablonu Container*.

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

## <a name="front_insert_iteratorfront_insert_iterator"></a><a name="front_insert_iterator"></a>front_insert_iterator::front_insert_iterator

Tworzy iterator, który może wstawić elementy z przodu określonego obiektu kontenera.

```cpp
explicit front_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Obiekt kontenera, `front_insert_iterator` do którego ma wstawić elementy.

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

## <a name="front_insert_iteratoroperator"></a><a name="op_star"></a>front_insert_iterator::operator\*

Dereferences wstaw iteratora zwraca element, który adresuje.

```cpp
front_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca wartość elementu adresowane.

### <a name="remarks"></a>Uwagi

Służy do implementacji**wartości** ** \*iteratora iteratora** = wyrażenia wyjściowego . Jeśli `Iter` jest iteratorem, który adresuje element w sekwencji, a następnie ** \*iter** = **wartość** zastępuje ten element z wartością i nie zmienia całkowitą liczbę elementów w sekwencji.

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

## <a name="front_insert_iteratoroperator"></a><a name="op_add_add"></a>front_insert_iterator::operator++

Zwiększa do `back_insert_iterator` następnej lokalizacji, w której wartość może być przechowywana.

```cpp
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Adresowanie `front_insert_iterator` następnej lokalizacji, w której może być przechowywana wartość.

### <a name="remarks"></a>Uwagi

Operatory przedwcześnie i postincrementation zwracają ten sam wynik.

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

## <a name="front_insert_iteratoroperator"></a><a name="op_eq"></a>front_insert_iterator::operator=

Dołącza (wypycha) wartość z przodu kontenera.

```cpp
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Wartość, która ma zostać przypisana do kontenera.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ostatniego elementu wstawionego z przodu kontenera.

### <a name="remarks"></a>Uwagi

Pierwszy operator elementu `container.push_front( val)`członkowskiego ocenia `*this`, a następnie zwraca .

Drugi operator członkowski ocenia

`container->push_front((typename Container::value_type&&) val)`,

następnie `*this`zwraca .

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

## <a name="front_insert_iteratorreference"></a><a name="reference"></a>front_insert_iterator::odwołanie

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

## <a name="see-also"></a>Zobacz też

[\<>iteratora](../standard-library/iterator.md)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)

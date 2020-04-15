---
title: insert_iterator — Klasa
ms.date: 11/04/2016
f1_keywords:
- iterator/std::insert_iterator
- iterator/std::insert_iterator::container_type
- iterator/std::insert_iterator::reference
helpviewer_keywords:
- std::insert_iterator [C++]
- std::insert_iterator [C++], container_type
- std::insert_iterator [C++], reference
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
ms.openlocfilehash: 2865db023425fa301ad5440a0dc8ed491213f33f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368053"
---
# <a name="insert_iterator-class"></a>insert_iterator — Klasa

Opisuje adapter iteratora, który spełnia wymagania iteratora danych wyjściowych. Wstawia (a nie zastępuje) elementy do sekwencji i w ten sposób zapewnia semantykę, która różni się od semantyki zastępowania, dostarczanej przez iteratory kontenerów asocjacyjnych i sekwencji C++. Klasa `insert_iterator` jest templatized na typ kontenera są dostosowywane.

## <a name="syntax"></a>Składnia

```cpp
template <class Container>
class insert_iterator;
```

### <a name="parameters"></a>Parametry

*Kontenera*\
Typ pojemnika, do którego elementy mają `insert_iterator`być wstawiane przez plik .

## <a name="remarks"></a>Uwagi

Kontener `Container` typu musi spełniać wymagania dla kontenera o zmiennym rozmiarze i mieć funkcję `Container::iterator` elementów członkowskich wstawiania dwóch argumentów, w której parametry są typu i `Container::value_type` który zwraca typ `Container::iterator`. Sekwencja biblioteki standardowej języka C++ i posortowane kontenery `insert_iterator`zespolone spełniają te wymagania i mogą być dostosowywane do użytku z s. Dla kontenerów asocjacyjnych argument pozycji jest traktowany jako wskazówka, która ma potencjał, aby zwiększyć lub zmniejszyć wydajność w zależności od tego, jak dobra jest to wskazówka. Musi `insert_iterator` być zawsze zainicjowany za pomocą jego kontenera.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[insert_iterator](#insert_iterator)|Konstruuje `insert_iterator` element, który wstawia element do określonego położenia w kontenerze.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który reprezentuje kontener, w którym ma być przeprowadzone ogólne wstawienie.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator*](#op_star)|Dereferencing operator używany do implementacji wyrażenia `i`  =  `x` iteratora danych wyjściowych * dla ogólnego wstawiania.|
|[operator++](#op_add_add)|Zwiększa do `insert_iterator` następnej lokalizacji, w której wartość może być przechowywana.|
|[operator=](#op_eq)|Operator przypisania używany do implementacji `i`  =  `x` wyrażenia iteratora wyjściowego * dla ogólnego wstawiania.|

## <a name="requirements"></a>Wymagania

**Nagłówek** \<:> iteratora

**Przestrzeń nazw:** std

## <a name="insert_iteratorcontainer_type"></a><a name="container_type"></a>insert_iterator::container_type

Typ, który reprezentuje kontener, w którym ma być przeprowadzone ogólne wstawienie.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru *szablonu Container*.

### <a name="example"></a>Przykład

```cpp
// insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   insert_iterator<list<int> >::container_type L2 = L1;
   inserter ( L2, L2.end ( ) ) = 20;
   inserter ( L2, L2.end ( ) ) = 10;
   inserter ( L2, L2.begin ( ) ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 20 10 ).
*/
```

## <a name="insert_iteratorinsert_iterator"></a><a name="insert_iterator"></a>insert_iterator::insert_iterator

Konstruuje `insert_iterator` element, który wstawia element do określonego położenia w kontenerze.

```cpp
insert_iterator(Container& _Cont, typename Container::iterator _It);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Kontener, do `insert_iterator` którego ma wstawić elementy.

*_It*\
Położenie wstawienia.

### <a name="remarks"></a>Uwagi

Wszystkie kontenery mają funkcję elementu `insert_iterator`członkowskiego wstawiać wywołaną przez . W przypadku kontenerów zespolonych parametr position jest jedynie sugestią. Funkcja insertera zapewnia wygodny sposób wstawiania do wartości.

### <a name="example"></a>Przykład

```cpp
// insert_iterator_insert_iterator.cpp
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
   for (i = 1 ; i < 4 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   inserter ( L, L.begin ( ) ) = 2;

   // Alternatively, you may use the template version
   insert_iterator< list < int> > Iter(L, L.end ( ) );
*Iter = 300;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( 10 20 30 ).
After the insertions, the list L is:
( 2 10 20 30 300 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_star"></a>insert_iterator::operator*

Dereferences wstawić iteratora zwracając element jest adresy.

```cpp
insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca wartość elementu adresowane.

### <a name="remarks"></a>Uwagi

Służy do implementacji**wartości** ** \*iteratora iteratora** = wyrażenia wyjściowego . Jeśli `Iter` jest iteratorem, który adresuje element w sekwencji, a następnie ** \*iter** = **wartość** zastępuje ten element z wartością i nie zmienia całkowitą liczbę elementów w sekwencji.

### <a name="example"></a>Przykład

```cpp
// insert_iterator_op_deref.cpp
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
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
*Iter = 10;
*Iter = 20;
*Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_add_add"></a>insert_iterator::operator++

Zwiększa do `insert_iterator` następnej lokalizacji, w której wartość może być przechowywana.

```cpp
insert_iterator<Container>& operator++();

insert_iterator<Container> operator++(int);
```

### <a name="parameters"></a>Parametry

Adresowanie `insert_iterator` następnej lokalizacji, w której może być przechowywana wartość.

### <a name="remarks"></a>Uwagi

Operatory przedwcześnie i postincrementation zwracają ten sam wynik.

### <a name="example"></a>Przykład

```cpp
// insert_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 5 ; ++i )
   {
      vec.push_back (  i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   insert_iterator<vector<int> > ii ( vec, vec.begin ( ) );
*ii = 30;
   ii++;
*ii = 40;
   ii++;
*ii = 50;

   cout << "After the insertions, the vector vec becomes:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The vector vec is:
( 1 2 3 4 ).
After the insertions, the vector vec becomes:
( 30 40 50 1 2 3 4 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_eq"></a>insert_iterator::operator=

Wstawia wartość do kontenera i zwraca iterator zaktualizowany, aby wskazać nowy element.

```cpp
insert_iterator<Container>& operator=(
    typename Container::const_reference val,);

insert_iterator<Container>& operator=(
    typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Wartość, która ma zostać przypisana do kontenera.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu wstawionego do pojemnika.

### <a name="remarks"></a>Uwagi

Pierwszy operator elementu członkowskiego ocenia

`Iter = container->insert(Iter, val)`;

`++Iter;`

następnie `*this`zwraca .

Drugi operator członkowski ocenia

`Iter = container->insert(Iter, std::move(val));`

`++Iter;`

następnie `*this`zwraca .

### <a name="example"></a>Przykład

```cpp
// insert_iterator_op_assign.cpp
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
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
*Iter = 10;
*Iter = 20;
*Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="insert_iteratorreference"></a><a name="reference"></a>insert_iterator::odwołanie

Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu sekwencji kontrolowane przez skojarzony kontener.

### <a name="example"></a>Przykład

```cpp
// insert_iterator_container_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   insert_iterator<list<int> > iivIter( L , L.begin ( ) );
*iivIter = 10;
*iivIter = 20;
*iivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++ )
      cout << *LIter << " ";
   cout << ")." << endl;

   insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 10 20 30 ).
The first element in the list L is: 10.
*/
```

## <a name="see-also"></a>Zobacz też

[\<>iteratora](../standard-library/iterator.md)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)

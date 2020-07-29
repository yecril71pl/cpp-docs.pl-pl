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
ms.openlocfilehash: 530168f5e259934f7d614b305e6ac1092ba68f4d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233161"
---
# <a name="insert_iterator-class"></a>insert_iterator — Klasa

Opisuje adapter iteratora, który spełnia wymagania iteratora danych wyjściowych. Wstawia (a nie zastępuje) elementy do sekwencji i w ten sposób zapewnia semantykę, która różni się od semantyki zastępowania, dostarczanej przez iteratory kontenerów asocjacyjnych i sekwencji C++. `insert_iterator`Klasa jest szablonowana dla typu dostosowanego kontenera.

## <a name="syntax"></a>Składnia

```cpp
template <class Container>
class insert_iterator;
```

### <a name="parameters"></a>Parametry

*Wbudowane*\
Typ kontenera, do którego elementy mają być wstawiane przez `insert_iterator` .

## <a name="remarks"></a>Uwagi

Kontener typu `Container` musi spełniać wymagania dotyczące kontenera o zmiennym rozmiarze i mieć dwuargumentową funkcję członkowską INSERT, gdzie parametry są typu `Container::iterator` i `Container::value_type` i zwracają typ `Container::iterator` . Sekwencja standardowej biblioteki języka C++ i posortowane Kontenery asocjacyjne spełniają te wymagania i można je dostosować do użycia z usługą `insert_iterator` s. Dla kontenerów asocjacyjnych argument pozycji jest traktowany jako wskazówka, która ma potencjał, aby zwiększyć lub zmniejszyć wydajność w zależności od tego, jak dobra jest to wskazówka. Element `insert_iterator` musi być zawsze zainicjowany przy użyciu jego kontenera.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[insert_iterator](#insert_iterator)|Tworzy obiekt `insert_iterator` , który wstawia element do określonej pozycji w kontenerze.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który reprezentuje kontener, w którym ma być przeprowadzone ogólne wstawienie.|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[zakład](#op_star)|Operator dereferencji używany do implementowania wyrażenia iteratora danych wyjściowych `i`  =  `x` dla ogólnego wstawiania.|
|[operator + +](#op_add_add)|Zwiększa `insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.|
|[operator =](#op_eq)|Operator przypisania używany do implementowania wyrażenia iteratora danych wyjściowych `i`  =  `x` dla ogólnego wstawiania.|

## <a name="requirements"></a>Wymagania

**Nagłówek**:\<iterator>

**Przestrzeń nazw:** std

## <a name="insert_iteratorcontainer_type"></a><a name="container_type"></a>insert_iterator:: container_type

Typ, który reprezentuje kontener, w którym ma być przeprowadzone ogólne wstawienie.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla *kontenera*parametrów szablonu.

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

## <a name="insert_iteratorinsert_iterator"></a><a name="insert_iterator"></a>insert_iterator:: insert_iterator

Tworzy obiekt `insert_iterator` , który wstawia element do określonej pozycji w kontenerze.

```cpp
insert_iterator(Container& _Cont, typename Container::iterator _It);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Kontener, do którego `insert_iterator` ma zostać wstawiony element.

*_It*\
Pozycja wstawiania.

### <a name="remarks"></a>Uwagi

Wszystkie kontenery mają funkcję INSERT member o nazwie `insert_iterator` . W przypadku kontenerów asocjacyjnych parametr pozycji jest tylko sugestią. Funkcja Inserter zapewnia wygodną metodę wstawiania do wartości.

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

## <a name="insert_iteratoroperator"></a><a name="op_star"></a>insert_iterator:: operator *

Odwołuje się do iteratora INSERT zwracający element to addresss.

```cpp
insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca wartość elementu, do którego się odnosi.

### <a name="remarks"></a>Uwagi

Służy do implementowania wyrażenia iteratora danych wyjściowych ** \* ITER**  =  **value**. Jeśli `Iter` jest iteratorem, który dotyczy elementu w sekwencji, a następnie ** \* ITER**  =  **wartość** zastępuje ten element wartością i nie zmienia łącznej liczby elementów w sekwencji.

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

## <a name="insert_iteratoroperator"></a><a name="op_add_add"></a>insert_iterator:: operator + +

Zwiększa `insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.

```cpp
insert_iterator<Container>& operator++();

insert_iterator<Container> operator++(int);
```

### <a name="parameters"></a>Parametry

`insert_iterator`Adresowanie następnej lokalizacji, w której może być przechowywana wartość.

### <a name="remarks"></a>Uwagi

Operatory przedrastające i postincrementation zwracają ten sam wynik.

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

## <a name="insert_iteratoroperator"></a><a name="op_eq"></a>insert_iterator:: operator =

Wstawia wartość do kontenera i zwraca iterator zaktualizowany, aby wskazywał nowy element.

```cpp
insert_iterator<Container>& operator=(
    typename Container::const_reference val,);

insert_iterator<Container>& operator=(
    typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

*użyte*\
Wartość, która ma zostać przypisana do kontenera.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu wstawionego do kontenera.

### <a name="remarks"></a>Uwagi

Obliczany jest pierwszy operator członkowski

`Iter = container->insert(Iter, val)`;

`++Iter;`

następnie zwraca wartość **`*this`** .

Drugi operator elementu członkowskiego oblicza

`Iter = container->insert(Iter, std::move(val));`

`++Iter;`

następnie zwraca wartość **`*this`** .

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

## <a name="insert_iteratorreference"></a><a name="reference"></a>insert_iterator:: Reference

Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu sekwencji kontrolowanego przez skojarzony kontener.

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

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)

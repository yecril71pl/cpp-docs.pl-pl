---
title: back_insert_iterator — Klasa
ms.date: 11/04/2016
f1_keywords:
- iterator/std::back_insert_iterator
- iterator/std::back_insert_iterator::container_type
- iterator/std::back_insert_iterator::reference
helpviewer_keywords:
- std::back_insert_iterator [C++]
- std::back_insert_iterator [C++], container_type
- std::back_insert_iterator [C++], reference
ms.assetid: a1ee07f2-cf9f-46a1-8608-cfaf207f9713
ms.openlocfilehash: 0a518253c28d89de6eeed51e152e11bfcb8bb969
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203886"
---
# <a name="back_insert_iterator-class"></a>back_insert_iterator — Klasa

Opisuje adapter iteratora, który spełnia wymagania iteratora danych wyjściowych. Wstawia (a nie zastępuje) elementy do tylnego końca sekwencji i w ten sposób zapewnia semantykę, która różni się od semantyki zastępowania, dostarczanej przez iteratory kontenerów sekwencji C++. `back_insert_iterator`Klasa jest szablonowana w typie kontenera.

## <a name="syntax"></a>Składnia

```cpp
template <class Container>
class back_insert_iterator;
```

### <a name="parameters"></a>Parametry

*Wbudowane*\
Typ kontenera do tyłu elementów, które mają zostać wstawione przez `back_insert_iterator` .

## <a name="remarks"></a>Uwagi

Kontener musi spełniać wymagania dla sekwencji wstawiania na tył, gdzie jest możliwe wstawianie elementów na koniec sekwencji w amortyzowanym stałym czasie. Kontenery sekwencji standardowej biblioteki języka C++ zdefiniowane przez [klasę deque](../standard-library/deque-class.md), [klasy list](../standard-library/list-class.md) i [klasy Vector](../standard-library/vector-class.md) zapewniają potrzebną `push_back` funkcję członkowską i spełniają te wymagania. Te trzy kontenery oraz ciągi mogą być dostosowane do użycia z parametrami `back_insert_iterator` s. Element A `back_insert_iterator` musi zawsze być zainicjowany przy użyciu jego kontenera.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[back_insert_iterator](#back_insert_iterator)|Tworzy `back_insert_iterator` element, który wstawia elementy po ostatnim elemencie w kontenerze.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który dostarcza kontener dla `back_insert_iterator` .|
|[odwoła](#reference)|Typ, który zawiera odwołanie do `back_insert_iterator` .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[zakład](#op_star)|Operator dereferencji używany do implementowania wyrażenia iteratora danych wyjściowych \* `i`  =  `x` dla wstawiania z tyłu.|
|[operator + +](#op_add_add)|Zwiększa `back_insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.|
|[operator =](#op_eq)|Operator przypisania używany do implementowania wyrażenia iteratora danych wyjściowych \* `i`  =  `x` dla wstawiania z tyłu.|

## <a name="requirements"></a>Wymagania

**Nagłówek**:\<iterator>

**Przestrzeń nazw:** std

## <a name="back_insert_iteratorback_insert_iterator"></a><a name="back_insert_iterator"></a>back_insert_iterator:: back_insert_iterator

Tworzy `back_insert_iterator` element, który wstawia elementy po ostatnim elemencie w kontenerze.

```cpp
explicit back_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Kontener, do którego `back_insert_iterator` ma zostać wstawiony element.

### <a name="return-value"></a>Wartość zwracana

A `back_insert_iterator` dla kontenera parametrów.

### <a name="example"></a>Przykład

```cpp
// back_insert_iterator_back_insert_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions with member function
   back_inserter ( vec ) = 40;
   back_inserter ( vec ) = 50;

   // Alternatively, insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 600;
   backiter++;
*backiter = 700;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 1 2 3 ).
After the insertions, the vector vec is: ( 1 2 3 40 50 600 700 ).
```

## <a name="back_insert_iteratorcontainer_type"></a><a name="container_type"></a>back_insert_iterator:: container_type

Typ, który dostarcza kontener dla `back_insert_iterator` .

```cpp
typedef Container
container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla **kontenera**parametrów szablonu.

### <a name="example"></a>Przykład

```cpp
// back_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back (  i );
   }

   vector <int>::iterator vIter;
   cout << "The original vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> >::container_type vec1 = vec;
   back_inserter ( vec1 ) = 40;

   cout << "After the insertion, the vector is: ( ";
   for ( vIter = vec1.begin ( ) ; vIter != vec1.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector vec is: ( 1 2 3 ).
After the insertion, the vector is: ( 1 2 3 40 ).
```

## <a name="back_insert_iteratoroperator"></a><a name="op_star"></a>back_insert_iterator:: operator\*

Operator dereferencji używany do implementowania wyrażenia iteratora danych wyjściowych \* *i*  =  *x*.

```cpp
back_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu wstawionego w tylnej części kontenera.

### <a name="remarks"></a>Uwagi

Służy do implementowania wyrażenia iteratora danych wyjściowych ** \* ITER**  =  **value**. Jeśli **ITER** jest iteratorem, który odnosi się do elementu w sekwencji, a następnie ** \* ITER**  =  **wartość** zastępuje ten element wartością i nie zmienia łącznej liczby elementów w sekwencji.

### <a name="example"></a>Przykład

```cpp
// back_insert_iterator_back_insert.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 10;
   backiter++;      // Increment to the next element
*backiter = 20;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The vector vec is: ( 1 2 3 ).
After the insertions, the vector vec becomes: ( 1 2 3 10 20 ).
```

## <a name="back_insert_iteratoroperator"></a><a name="op_add_add"></a>back_insert_iterator:: operator + +

Zwiększa `back_insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.

```cpp
back_insert_iterator<Container>& operator++();
back_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

`back_insert_iterator`Adresowanie następnej lokalizacji, w której może być przechowywana wartość.

### <a name="remarks"></a>Uwagi

Operatory przedrastające i postincrementation zwracają ten sam wynik.

### <a name="example"></a>Przykład

```cpp
// back_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 3 ; ++i )
   {
      vec.push_back ( 10 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 30;
   backiter++;      // Increment to the next element
*backiter = 40;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The vector vec is: ( 10 20 ).
After the insertions, the vector vec becomes: ( 10 20 30 40 ).
```

## <a name="back_insert_iteratoroperator"></a><a name="op_eq"></a>back_insert_iterator:: operator =

Dołącza lub wypycha wartość na zapleczu kontenera.

```cpp
back_insert_iterator<Container>& operator=(typename Container::const_reference val);
back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

*użyte*\
Wartość, która ma zostać wstawiona do kontenera.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ostatniego elementu wstawionego z tyłu kontenera.

### <a name="remarks"></a>Uwagi

Pierwszy operator elementu członkowskiego oblicza `Container.push_back( val)` ,

następnie zwraca wartość **`*this`** . Drugi operator elementu członkowskiego oblicza

`container->push_back((typename Container::value_type&&)val)`,

następnie zwraca wartość **`*this`** .

### <a name="example"></a>Przykład

```cpp
// back_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 10;
   backiter++;      // Increment to the next element
*backiter = 20;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

## <a name="back_insert_iteratorreference"></a><a name="reference"></a>back_insert_iterator:: Reference

Typ, który zawiera odwołanie do `back_insert_iterator` .

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu sekwencji kontrolowanego przez skojarzony kontener.

### <a name="example"></a>Przykład

```cpp
// back_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> >::reference
        RefLast = *(vec.end ( ) - 1 );
   cout << "The last element in the vector vec is: "
        << RefLast << "." << endl;
}
```

```Output
The vector vec is: ( 1 2 3 ).
The last element in the vector vec is: 3.
```

## <a name="see-also"></a>Zobacz też

[\<iterator>](../standard-library/iterator.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)

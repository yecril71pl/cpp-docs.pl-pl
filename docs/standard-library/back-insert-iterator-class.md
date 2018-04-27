---
title: back_insert_iterator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iterator/std::back_insert_iterator
- iterator/std::back_insert_iterator::container_type
- iterator/std::back_insert_iterator::reference
dev_langs:
- C++
helpviewer_keywords:
- std::back_insert_iterator [C++]
- std::back_insert_iterator [C++], container_type
- std::back_insert_iterator [C++], reference
ms.assetid: a1ee07f2-cf9f-46a1-8608-cfaf207f9713
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 770734398074c8de063f4ac4b52d654bd92365cc
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="backinsertiterator-class"></a>back_insert_iterator — Klasa

Opisuje adapter iteratora, który spełnia wymagania iteratora danych wyjściowych. Wstawia (a nie zastępuje) elementy do tylnego końca sekwencji i w ten sposób zapewnia semantykę, która różni się od semantyki zastępowania, dostarczanej przez iteratory kontenerów sekwencji C++. `back_insert_iterator` Klasy jest którego ma zastosowany szablon na typ kontenera.

## <a name="syntax"></a>Składnia

```cpp
template <class Container>
class back_insert_iterator;
```

### <a name="parameters"></a>Parametry

`Container` Typ kontenera do tyłu elementy, które mają zostać wstawione przez `back_insert_iterator`.

## <a name="remarks"></a>Uwagi

Kontener musi spełniać wymagania dla sekwencji wstawiania na tył, gdzie jest możliwe wstawianie elementów na koniec sekwencji w amortyzowanym stałym czasie. Standardowa biblioteka C++ sekwencji kontenery zdefiniowane przez [deque — klasa](../standard-library/deque-class.md), [list — klasa](../standard-library/list-class.md) i [vector — klasa](../standard-library/vector-class.md) Podaj wymagane `push_back` funkcji członkowskiej i spełnia te wymagania. Te trzy kontenery, a także ciągi każdego można dostosować do użycia z `back_insert_iterator`s. A `back_insert_iterator` zawsze musi zostać zainicjowany z jego kontenera.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[back_insert_iterator](#back_insert_iterator)|Konstruuje `back_insert_iterator` która wstawia elementy za ostatnim elementem w kontenerze.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który udostępnia kontener dla `back_insert_iterator`.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do `back_insert_iterator`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator *](#op_star)|Operator usuwania odwołań używaną do zaimplementowania wyrażenia iteratora dane wyjściowe * `i`  =  `x` do tyłu wstawiania.|
|[operator++](#op_add_add)|Zwiększa `back_insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.|
|[operator=](#op_eq)|Operator przypisania używaną do zaimplementowania wyrażenia iteratora dane wyjściowe * `i`  =  `x` do tyłu wstawiania.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<iteratora >

**Namespace:** Standard

## <a name="back_insert_iterator"></a>  back_insert_iterator::back_insert_iterator

Konstruuje `back_insert_iterator` która wstawia elementy za ostatnim elementem w kontenerze.

```cpp
explicit back_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Parametry

`_Cont` Kontener który `back_insert_iterator` ma element do wstawienia.

### <a name="return-value"></a>Wartość zwracana

A `back_insert_iterator` kontenera parametru.

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

## <a name="container_type"></a>  back_insert_iterator::container_type

Typ, który udostępnia kontener dla `back_insert_iterator`.

```cpp
typedef Container
container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **kontenera**.

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

## <a name="op_star"></a>  back_insert_iterator::operator *

Operator usuwania odwołań używaną do zaimplementowania wyrażenia iteratora dane wyjściowe \* *i* = *x*.

```cpp
back_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu dodaje tyłu kontenera.

### <a name="remarks"></a>Uwagi

Używane do implementowania wyrażenia iteratora dane wyjściowe  **\*Iter** = **wartość**. Jeśli **Iter** jest iteratora, którego dotyczy elementu w sekwencji, następnie  **\*Iter** = **wartość** zamienia wartość tego elementu, a nie Zmień łączna liczba elementów w sekwencji.

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

## <a name="op_add_add"></a>  back_insert_iterator::operator ++

Zwiększa `back_insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.

```cpp
back_insert_iterator<Container>& operator++();
back_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

A `back_insert_iterator` adresowania następnej lokalizacji, w której może być przechowywana wartość.

### <a name="remarks"></a>Uwagi

Operatory zarówno preincrementation i postincrementation zwracać ten sam rezultat.

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

## <a name="op_eq"></a>  back_insert_iterator::operator =

Dołącza lub wypychanie wartości na zaplecza kontenera.

```cpp
back_insert_iterator<Container>& operator=(typename Container::const_reference val);
back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

`val` Wartość, która ma zostać wstawiony do kontenera.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ostatniego elementu dodaje tyłu kontenera.

### <a name="remarks"></a>Uwagi

Oblicza pierwszy operator członkowski `Container.push_back( val)`,

Zwraca `*this`. Oblicza drugi operator elementu członkowskiego

`container->push_back((typename Container::value_type&&)val)`,

Zwraca `*this`.

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

## <a name="reference"></a>  back_insert_iterator::Reference

Typ, który zawiera odwołanie do `back_insert_iterator`.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Uwagi

Typ w tym artykule opisano odwołanie do elementu sekwencji kontrolowane przez skojarzony kontenera.

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

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>

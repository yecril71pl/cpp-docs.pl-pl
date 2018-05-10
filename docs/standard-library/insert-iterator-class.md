---
title: insert_iterator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/std::insert_iterator
- iterator/std::insert_iterator::container_type
- iterator/std::insert_iterator::reference
dev_langs:
- C++
helpviewer_keywords:
- std::insert_iterator [C++]
- std::insert_iterator [C++], container_type
- std::insert_iterator [C++], reference
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6eb1eec82e7f9e39f508bd0c9559cec787f6ec9a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="insertiterator-class"></a>insert_iterator — Klasa

Opisuje adapter iteratora, który spełnia wymagania iteratora danych wyjściowych. Wstawia (a nie zastępuje) elementy do sekwencji i w ten sposób zapewnia semantykę, która różni się od semantyki zastępowania, dostarczanej przez iteratory kontenerów asocjacyjnych i sekwencji C++. `insert_iterator` Klasy jest którego ma zastosowany szablon na typ kontenera dostosowuje się.

## <a name="syntax"></a>Składnia

```cpp
template <class Container>
class insert_iterator;
```

### <a name="parameters"></a>Parametry

`Container` Typ kontenera, w którym mają zostać wstawione przez elementy `insert_iterator`.

## <a name="remarks"></a>Uwagi

Kontener typu **kontenera** musi spełniać wymagania dotyczące kontener o zmiennej długości i mieć Wstaw dwa argumentu funkcji członkowskiej, gdzie parametry są typu **Container::iterator** i **Container::value_type** i który zwraca typ **Container::iterator**. Sekwencja standardowa biblioteka C++ posortowane kontenery asocjacyjnej spełnia wymagania i mogą być dostosowywane do użycia z `insert_iterator`s. Dla kontenerów asocjacyjnych argument pozycji jest traktowany jako wskazówka, która ma potencjał, aby zwiększyć lub zmniejszyć wydajność w zależności od tego, jak dobra jest to wskazówka. `insert_iterator` Zawsze musi zostać zainicjowany z jego kontenera.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[insert_iterator](#insert_iterator)|Konstruuje `insert_iterator` która wstawia element do określonej pozycji w kontenerze.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który reprezentuje kontener, w którym ma być przeprowadzone ogólne wstawienie.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator *](#op_star)|Operator usuwania odwołań używaną do zaimplementowania wyrażenia iteratora dane wyjściowe * `i`  =  `x` dla ogólnych wstawiania.|
|[operator++](#op_add_add)|Zwiększa `insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.|
|[operator=](#op_eq)|Operator przypisania używaną do zaimplementowania wyrażenia iteratora dane wyjściowe * `i`  =  `x` dla ogólnych wstawiania.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<iteratora >

**Namespace:** Standard

## <a name="container_type"></a>  insert_iterator::container_type

Typ, który reprezentuje kontener, w którym ma być przeprowadzone ogólne wstawienie.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **kontenera**.

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
\* Output:
The list L2 is: ( 40 20 10 ).
*\
```

## <a name="insert_iterator"></a>  insert_iterator::insert_iterator

Konstruuje `insert_iterator` która wstawia element do określonej pozycji w kontenerze.

```cpp
insert_iterator(Container& _Cont, typename Container::iterator _It);
```

### <a name="parameters"></a>Parametry

`_Cont` Kontener, do którego `insert_iterator` jest, aby wstawić elementów.

`_It` Pozycja dla wstawiania.

### <a name="remarks"></a>Uwagi

Wszystkie kontenery mają funkcji członkowskiej insert wywoływane przez `insert_iterator`. Dla kontenerów asocjacyjnej parametr pozycji jest jedynie sugestię. Funkcja Wstawianie oferują wygodny sposób wstawić wartości.

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
\* Output:
The list L is:
 ( 10 20 30 ).
After the insertions, the list L is:
 ( 2 10 20 30 300 ).
*\
```

## <a name="op_star"></a>  insert_iterator::operator *

Wyłuskań iteratora insert, zwracając się, że element jest adresów.

```cpp
insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca wartość elementu problemu.

### <a name="remarks"></a>Uwagi

Używane do implementowania wyrażenia iteratora dane wyjściowe  **\*Iter** = **wartość**. Jeśli **Iter** jest iteratora, którego dotyczy elementu w sekwencji, następnie  **\*Iter** = **wartość** zamienia wartość tego elementu, a nie Zmień łączna liczba elementów w sekwencji.

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
\* Output:
The original list L is:
 ( 0 2 4 6 ).
After the insertions, the list L is:
 ( 10 20 30 0 2 4 6 ).
*\
```

## <a name="op_add_add"></a>  insert_iterator::operator ++

Zwiększa **insert_iterator —** do następnej lokalizacji, w której może być przechowywana wartość.

```cpp
insert_iterator<Container>& operator++();

insert_iterator<Container> operator++(int);
```

### <a name="parameters"></a>Parametry

A `insert_iterator` adresowania następnej lokalizacji, w której może być przechowywana wartość.

### <a name="remarks"></a>Uwagi

Operatory zarówno preincrementation i postincrementation zwracać ten sam rezultat.

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
\* Output:
The vector vec is:
 ( 1 2 3 4 ).
After the insertions, the vector vec becomes:
 ( 30 40 50 1 2 3 4 ).
*\
```

## <a name="op_eq"></a>  insert_iterator::operator =

Wstawia wartości w kontenerze i zwraca iteratora zaktualizowane, aby wskazywały nowy element.

```cpp
insert_iterator<Container>& operator=(
    typename Container::const_reference val,);

insert_iterator<Container>& operator=(
    typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

`val` Wartość do przypisania do kontenera.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu do kontenera.

### <a name="remarks"></a>Uwagi

Oblicza pierwszy operator elementu członkowskiego

`Iter = container->insert(Iter, val)`;

`++Iter;`

Zwraca `*this`.

Oblicza drugi operator elementu członkowskiego

`Iter = container->insert(Iter, std::move(val));`

`++Iter;`

Zwraca `*this`.

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
\* Output:
The original list L is:
 ( 0 2 4 6 ).
After the insertions, the list L is:
 ( 10 20 30 0 2 4 6 ).
*\
```

## <a name="reference"></a>  insert_iterator::Reference

Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Uwagi

Typ w tym artykule opisano odwołanie do elementu sekwencji kontrolowane przez skojarzony kontenera.

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
\* Output:
The list L is: ( 10 20 30 ).
The first element in the list L is: 10.
*\
```

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>

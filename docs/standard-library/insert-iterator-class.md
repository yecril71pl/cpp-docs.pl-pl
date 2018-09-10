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
ms.openlocfilehash: 6011bd8f413a2e0a849e2ef9ba7c5bc229913c41
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318840"
---
# <a name="insertiterator-class"></a>insert_iterator — Klasa

Opisuje adapter iteratora, który spełnia wymagania iteratora danych wyjściowych. Wstawia (a nie zastępuje) elementy do sekwencji i w ten sposób zapewnia semantykę, która różni się od semantyki zastępowania, dostarczanej przez iteratory kontenerów asocjacyjnych i sekwencji C++. `insert_iterator` Klasy jest szablonowana na typie adaptowanego kontenera.

## <a name="syntax"></a>Składnia

```cpp
template <class Container>
class insert_iterator;
```

### <a name="parameters"></a>Parametry

*Kontener*<br/>
Typ kontenera, do którego elementy mają zostać wstawione przez `insert_iterator`.

## <a name="remarks"></a>Uwagi

Kontener typu `Container` musi spełniać wymagania dla kontenera zmiennym rozmiarze i mieć dwuargumentową wstawiania funkcji składowej, gdzie parametry są typu `Container::iterator` i `Container::value_type` i który zwraca typ `Container::iterator`. Sekwencja standardowej biblioteki języka C++ i sortowane kontenery asocjacyjne spełniają te wymagania i mogą być dostosowane do użytku z `insert_iterator`s. Dla kontenerów asocjacyjnych argument pozycji jest traktowany jako wskazówka, która ma potencjał, aby zwiększyć lub zmniejszyć wydajność w zależności od tego, jak dobra jest to wskazówka. `insert_iterator` Zawsze musi zostać zainicjowany z jego kontenerem.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[insert_iterator](#insert_iterator)|Konstruuje `insert_iterator` który wstawia element do określonej pozycji w kontenerze.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[container_type](#container_type)|Typ, który reprezentuje kontener, w którym ma być przeprowadzone ogólne wstawienie.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator *](#op_star)|Operator dereferencji używany do implementowania wyrażenie iteratora wyjściowego * `i`  =  `x` dla ogólnego wstawiania.|
|[operator++](#op_add_add)|Zwiększa `insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.|
|[operator=](#op_eq)|Operator przypisania używany do implementowania wyrażenie iteratora wyjściowego * `i`  =  `x` dla ogólnego wstawiania.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<iterator >

**Namespace:** standardowe

## <a name="container_type"></a>  insert_iterator::container_type

Typ, który reprezentuje kontener, w którym ma być przeprowadzone ogólne wstawienie.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *kontenera*.

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

## <a name="insert_iterator"></a>  insert_iterator::insert_iterator

Konstruuje `insert_iterator` który wstawia element do określonej pozycji w kontenerze.

```cpp
insert_iterator(Container& _Cont, typename Container::iterator _It);
```

### <a name="parameters"></a>Parametry

*_Cont*<br/>
Kontener, do którego `insert_iterator` jest wstawianie elementów.

*_It*<br/>
Pozycja do wstawienia.

### <a name="remarks"></a>Uwagi

Wszystkie kontenery mają wstawienie funkcji elementu członkowskiego wywoływane przez `insert_iterator`. Działające na kontenerach asocjacyjnych parametr position jest jedynie sugestię. Inserter — funkcja oferuje wygodny sposób do wstawienia wartości.

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

## <a name="op_star"></a>  insert_iterator::operator *

Wyłuskań iteratorów wstawiania zwróci element jest adresów.

```cpp
insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Element członkowski funkcji zwraca wartość elementu wspominanego.

### <a name="remarks"></a>Uwagi

Używany do implementowania wyrażenia iteratora danych wyjściowych  **\*Iter** = **wartość**. Jeśli `Iter` jest iterator odnoszący się do elementu w sekwencji, następnie  **\*Iter** = **wartość** zamienia wartość tego elementu i nie zmienia łączną liczbę elementy w sekwencji.

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

## <a name="op_add_add"></a>  insert_iterator::operator ++

Zwiększa `insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.

```cpp
insert_iterator<Container>& operator++();

insert_iterator<Container> operator++(int);
```

### <a name="parameters"></a>Parametry

A `insert_iterator` adresowania następnej lokalizacji, w której może być przechowywana wartość.

### <a name="remarks"></a>Uwagi

Operatory preincrementation i postincrementation zwracać ten sam wynik.

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

## <a name="op_eq"></a>  insert_iterator::operator =

Wstawia wartości w kontenerze i zwraca iterator poinformowani o nowy element.

```cpp
insert_iterator<Container>& operator=(
    typename Container::const_reference val,);

insert_iterator<Container>& operator=(
    typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość do przypisania do kontenera.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu do kontenera.

### <a name="remarks"></a>Uwagi

Oblicza pierwszy operator członkowski

`Iter = container->insert(Iter, val)`;

`++Iter;`

Następnie zwraca `*this`.

Drugi operator składowej daje w wyniku

`Iter = container->insert(Iter, std::move(val));`

`++Iter;`

Następnie zwraca `*this`.

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

## <a name="reference"></a>  insert_iterator::Reference

Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje odwołanie do elementu sekwencji kontrolowanej przez skojarzony kontener.

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

[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>

---
title: '&lt;Lista&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::operator!=
- list/std::operator&gt;
- list/std::operator&gt;=
- list/std::operator&lt;
- list/std::operator&lt;=
- list/std::operator==
dev_langs:
- C++
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
helpviewer_keywords:
- std::operator!= (list)
- std::operator&gt; (list)
- std::operator&gt;= (list)
- std::operator&lt; (list)
- std::operator&lt;= (list)
- std::operator== (list)
ms.openlocfilehash: b2647cf836fb565115b8a582085b6108c01a3420
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltlistgt-operators"></a>&lt;Lista&gt; operatory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator! =

Testy, jeśli obiekt listy po lewej stronie operatora nie jest taki sam jak obiekt listy po prawej stronie.

```cpp
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **listy**.

`right` Obiekt typu **listy**.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** list nie są równe; **false** listy są równe.

### <a name="remarks"></a>Uwagi

Porównanie listę obiektów jest oparta na parowania porównanie ich elementów. Dwie listy są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

### <a name="example"></a>Przykład

```cpp
// list_op_ne.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
using namespace std;
list <int> c1, c2;
c1.push_back( 1 );
c2.push_back( 2 );

if ( c1 != c2 )
cout << "Lists not equal." << endl;
else
cout << "Lists equal." << endl;
}
\* Output:
Lists not equal.
*\
```

## <a name="op_lt"></a>  Operator&lt;

Testy, jeśli obiekt listy po lewej stronie operatora jest mniejsza niż obiekt listy po prawej stronie.

```cpp
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **listy**.

`right` Obiekt typu **listy**.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest mniejsza niż, ale nie równa liście po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie listę obiektów jest oparta na parowania porównanie ich elementów. Less — niż relacji między dwoma obiektami jest oparta na porównanie pierwszego pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// list_op_lt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "List c1 is less than list c2." << endl;
   else
      cout << "List c1 is not less than list c2." << endl;
}
\* Output:
List c1 is less than list c2.
*\
```

## <a name="op_lt_eq"></a>  Operator&lt;=

Testy, jeśli obiekt listy po lewej stronie operatora jest mniejsza niż lub równe obiekt listy po prawej stronie.

```cpp
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **listy**.

`right` Obiekt typu **listy**.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest mniejsza niż lub równa liście po prawej stronie operatora, w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie listę obiektów jest oparta na parowania porównanie ich elementów. Mniejsze niż lub równe do relacji między dwoma obiektami jest oparta na porównanie pierwszego pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// list_op_le.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "List c1 is less than or equal to list c2." << endl;
   else
      cout << "List c1 is greater than list c2." << endl;
}
\* Output:
List c1 is less than or equal to list c2.
*\
```

## <a name="op_eq_eq"></a>  operator ==

Testy, jeśli obiekt listy po lewej stronie operatora jest taki sam jak obiekt listy po prawej stronie.

```cpp
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **listy**.

`right` Obiekt typu **listy**.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest równa liście po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie listę obiektów jest oparta na parowania porównanie ich elementów. Dwie listy są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

### <a name="example"></a>Przykład

```cpp
// list_op_eq.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;

   list <int> c1, c2;
   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The lists are equal." << endl;
   else
      cout << "The lists are not equal." << endl;
}
\* Output:
The lists are equal.
*\
```

## <a name="op_gt"></a>  Operator&gt;

Testy, jeśli obiekt listy po lewej stronie operatora jest większy niż obiekt listy po prawej stronie.

```cpp
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **listy**.

`right` Obiekt typu **listy**.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest większa niż liście po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie listę obiektów jest oparta na parowania porównanie ich elementów. Większa-niż relacji między dwoma obiektami jest oparta na porównanie pierwszego pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// list_op_gt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "List c1 is greater than list c2." << endl;
   else
      cout << "List c1 is not greater than list c2." << endl;
}
\* Output:
List c1 is greater than list c2.
*\
```

## <a name="op_gt_eq"></a>  Operator&gt;=

Testy, jeśli obiekt listy po lewej stronie operatora jest większa niż lub równa obiekt listy po prawej stronie.

```cpp
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **listy**.

`right` Obiekt typu **listy**.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest większa niż lub równa liście po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie listę obiektów jest oparta na parowania porównanie ich elementów. Większa niż lub równa relacji między dwoma obiektami opiera się na porównanie pierwszego pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// list_op_ge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "List c1 is greater than or equal to list c2." << endl;
   else
      cout << "List c1 is less than list c2." << endl;
}
\* Output:
List c1 is greater than or equal to list c2.
*\
```

## <a name="see-also"></a>Zobacz także

[\<list>](../standard-library/list.md)<br/>

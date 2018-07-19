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
ms.openlocfilehash: ba77722abb28f246d305b44fb78379b2297ccc14
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965720"
---
# <a name="ltlistgt-operators"></a>&lt;Lista&gt; operatorów

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator! =

Sprawdza, czy obiekt listy po lewej stronie operatora nie jest równy obiektowi listy po prawej stronie.

```cpp
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie* obiektu typu `list`.

*prawy* obiektu typu `list`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** listy nie są równe; **false** list są równe.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami listy opiera się na parowania porównania ich elementów. Dwie listy są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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

Sprawdza, czy obiekt listy, po lewej stronie operatora jest mniejszy niż obiekt listy po prawej stronie.

```cpp
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie* obiektu typu `list`.

*prawy* obiektu typu `list`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli na liście po lewej stronie operatora jest mniejszy niż, ale nie równa listy po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami listy opiera się na parowania porównania ich elementów. Mniej-niż relacji między dwoma obiektami opiera się na porównanie pierwszy pary nierówne elementów.

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

Sprawdza, czy lista obiektów po lewej stronie operatora jest mniejszy niż lub równy obiektowi listy po prawej stronie.

```cpp
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie* obiektu typu `list`.

*prawy* obiektu typu `list`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest mniejszy niż lub równe do listy po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami listy opiera się na parowania porównania ich elementów. Mniejszą lub równą do relacji między dwoma obiektami opiera się na porównaniu pierwszy pary nierówne elementów.

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

Sprawdza, czy obiekt listy po lewej stronie operatora jest równy obiektowi listy po prawej stronie.

```cpp
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie* obiektu typu `list`.

*prawy* obiektu typu `list`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest równy listy po prawej stronie operatora, a w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami listy opiera się na parowania porównania ich elementów. Dwie listy są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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

Sprawdza, czy obiekt listy po lewej stronie operatora jest większy niż obiekt listy po prawej stronie.

```cpp
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie* obiektu typu `list`.

*prawy* obiektu typu `list`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest większy niż listy po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami listy opiera się na parowania porównania ich elementów. Większą-niż relacji między dwoma obiektami opiera się na porównanie pierwszy pary nierówne elementów.

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

Sprawdza, czy obiekt listy po lewej stronie operatora jest większy lub równy obiektowi listy po prawej stronie.

```cpp
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie* obiektu typu `list`.

*prawy* obiektu typu `list`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest większy niż lub równe do listy po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami listy opiera się na parowania porównania ich elementów. Większa lub równa relacji między dwoma obiektami opiera się na porównaniu pierwszy pary nierówne elementów.

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

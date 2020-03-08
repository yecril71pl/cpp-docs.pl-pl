---
title: Operatory &lt;list&gt;
ms.date: 11/04/2016
f1_keywords:
- list/std::operator!=
- list/std::operator&gt;
- list/std::operator&gt;=
- list/std::operator&lt;
- list/std::operator&lt;=
- list/std::operator==
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
helpviewer_keywords:
- std::operator!= (list)
- std::operator&gt; (list)
- std::operator&gt;= (list)
- std::operator&lt; (list)
- std::operator&lt;= (list)
- std::operator== (list)
ms.openlocfilehash: 7b0b7540c1b9a55140405a55e8e034f9c6ec646c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874443"
---
# <a name="ltlistgt-operators"></a>Operatory &lt;list&gt;

## <a name="op_neq"></a>operator! =

Testuje, czy obiekt listy po lewej stronie operatora nie jest równy obiektowi listy po prawej stronie.

```cpp
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `list`.

*prawa*\
Obiekt typu `list`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli listy nie są równe; **wartość false** , jeśli listy są równe.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami list jest oparte na porównaniu z przełączaniem ich elementów. Dwie listy są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

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
/* Output:
Lists not equal.
*/
```

## <a name="op_lt"></a>&lt; operatora

Testuje, czy obiekt listy po lewej stronie operatora jest mniejszy niż obiekt listy po prawej stronie.

```cpp
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `list`.

*prawa*\
Obiekt typu `list`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli lista po lewej stronie operatora jest mniejsza niż, ale nie równa liście po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami list jest oparte na porównaniu z przełączaniem ich elementów. Relacja mniejsza niż między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

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
/* Output:
List c1 is less than list c2.
*/
```

## <a name="op_lt_eq"></a>&lt;operatora =

Testuje, czy obiekt listy po lewej stronie operatora jest mniejszy niż lub równy obiektowi listy po prawej stronie.

```cpp
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `list`.

*prawa*\
Obiekt typu `list`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli lista po lewej stronie operatora jest mniejsza lub równa liście po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami list jest oparte na porównaniu z przełączaniem ich elementów. Mniejsza lub równa relacji między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

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
/* Output:
List c1 is less than or equal to list c2.
*/
```

## <a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt listy po lewej stronie operatora jest równy obiektowi listy po prawej stronie.

```cpp
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `list`.

*prawa*\
Obiekt typu `list`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli lista po lewej stronie operatora jest równa liście po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami list jest oparte na porównaniu z przełączaniem ich elementów. Dwie listy są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

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
/* Output:
The lists are equal.
*/
```

## <a name="op_gt"></a>&gt; operatora

Testuje, czy obiekt listy po lewej stronie operatora jest większy niż obiekt listy po prawej stronie.

```cpp
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `list`.

*prawa*\
Obiekt typu `list`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli lista po lewej stronie operatora jest większa niż lista po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami list jest oparte na porównaniu z przełączaniem ich elementów. Relacja większa niż między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

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
/* Output:
List c1 is greater than list c2.
*/
```

## <a name="op_gt_eq"></a>&gt;operatora =

Testuje, czy obiekt listy po lewej stronie operatora jest większy niż lub równy obiektowi listy po prawej stronie.

```cpp
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `list`.

*prawa*\
Obiekt typu `list`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli lista po lewej stronie operatora jest większa lub równa liście po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami list jest oparte na porównaniu z przełączaniem ich elementów. Większa lub równa relacji między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

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
/* Output:
List c1 is greater than or equal to list c2.
*/
```

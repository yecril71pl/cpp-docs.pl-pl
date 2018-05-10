---
title: '&lt;deque —&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- deque/std::operator!=
- deque/std::operator&gt;
- deque/std::operator&gt;=
- deque/std::operator&lt;
- deque/std::operator&lt;=
- deque/std::operator==
dev_langs:
- C++
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
helpviewer_keywords:
- std::operator!= (deque)
- std::operator&gt; (deque)
- std::operator&gt;= (deque)
- std::operator&lt; (deque)
- std::operator&lt;= (deque)
- std::operator== (deque)
ms.openlocfilehash: d4dfa6963e9c8194bd4ee589a1a0adced1f05d0d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ltdequegt-operators"></a>&lt;deque —&gt; operatory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator! =

Testy, jeśli obiekt deque — po lewej stronie operatora nie jest taki sam jak obiekt deque — po prawej stronie.

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `deque`.

`right` Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** deque — obiekty nie są równe; **false** deque — obiekty są równe.

### <a name="remarks"></a>Uwagi

Porównanie deque — obiekty opiera się na parowania porównanie ich elementów. Dwa deque — obiekty są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

### <a name="example"></a>Przykład

```cpp
// deque_op_ne.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 2 );

   if ( c1 != c2 )
      cout << "The deques are not equal." << endl;
   else
      cout << "The deques are equal." << endl;
}
\* Output:
The deques are not equal.
*\
```

## <a name="op_lt"></a>  Operator&lt;

Testy, jeśli obiekt deque — po lewej stronie operatora jest mniejsza niż obiekt deque — po prawej stronie.

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `deque`.

`right` Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli deque — po lewej stronie operatora jest mniejsza niż i nie równa deque — po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie deque — obiekty opiera się na parowania porównanie ich elementów. Less — niż relacji między dwoma obiektami jest oparta na porównanie pierwszego pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// deque_op_lt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "Deque c1 is less than deque c2." << endl;
   else
      cout << "Deque c1 is not less than deque c2." << endl;
}
\* Output:
Deque c1 is less than deque c2.
*\
```

## <a name="op_lt_eq"></a>  Operator&lt;=

Testy, jeśli deque — obiekty po lewej stronie operatora jest mniejsza niż lub równe obiektu deque — po prawej stronie.

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `deque`.

`right` Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli deque — po lewej stronie operatora jest mniejsza niż lub równa deque — po prawej stronie operatora, w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie deque — obiekty opiera się na parowania porównanie ich elementów. Mniejsze niż lub równe do relacji między dwoma obiektami jest oparta na porównanie pierwszego pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// deque_op_le.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "Deque c1 is less than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is greater than deque c2." << endl;
}
\* Output:
Deque c1 is less than or equal to deque c2.
*\

```

## <a name="op_eq_eq"></a>  operator ==

Testy, jeśli obiekt deque — po lewej stronie operatora jest taki sam jak obiekt deque — po prawej stronie.

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `deque`.

`right` Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli deque — po lewej stronie operatora jest równa deque — po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie deque — obiekty opiera się na parowania porównanie ich elementów. Dwa deques są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

### <a name="example"></a>Przykład

```cpp
// deque_op_eq.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;

   c1.push_back( 1 );
   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;
}
\* Output:
The deques are equal.
The deques are not equal.
*\

```

## <a name="op_gt"></a>  Operator&gt;

Testy, jeśli obiekt deque — po lewej stronie operatora jest większy niż obiekt deque — po prawej stronie.

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `deque`.

`right` Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli deque — po lewej stronie operatora jest większa niż deque — po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie deque — obiekty opiera się na parowania porównanie ich elementów. Większa-niż relacji między dwoma obiektami jest oparta na porównanie pierwszego pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// deque_op_gt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "Deque c1 is greater than deque c2." << endl;
   else
      cout << "Deque c1 is not greater than deque c2." << endl;
}
\* Output:
Deque c1 is greater than deque c2.
*\

```

## <a name="op_gt_eq"></a>  Operator&gt;=

Testy, jeśli obiekt deque — po lewej stronie operatora jest większa niż lub równa obiektu deque — po prawej stronie.

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `deque`.

`right` Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli deque — po lewej stronie operatora jest większa niż lub równa deque — po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie deque — obiekty opiera się na parowania porównanie ich elementów. Większa niż lub równa relacji między dwoma obiektami opiera się na porównanie pierwszego pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// deque_op_ge.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "Deque c1 is greater than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is less than deque c2." << endl;
}
\* Output:
Deque c1 is greater than or equal to deque c2.
*\
```

## <a name="see-also"></a>Zobacz także

[\<deque — >](../standard-library/deque.md)<br/>

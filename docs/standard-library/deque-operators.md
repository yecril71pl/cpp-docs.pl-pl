---
title: '&lt;deque —&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- deque/std::operator!=
- deque/std::operator&gt;
- deque/std::operator&gt;=
- deque/std::operator&lt;
- deque/std::operator&lt;=
- deque/std::operator==
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
helpviewer_keywords:
- std::operator!= (deque)
- std::operator&gt; (deque)
- std::operator&gt;= (deque)
- std::operator&lt; (deque)
- std::operator&lt;= (deque)
- std::operator== (deque)
ms.openlocfilehash: 868909ac4346a59cade3660f288a0f0e71bc4ed0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245659"
---
# <a name="ltdequegt-operators"></a>&lt;deque —&gt; operatorów

## <a name="op_neq"></a> operator! =

Sprawdza, czy obiekt deque po lewej stronie operatora nie jest równy obiektowi deque — po prawej stronie.

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt typu `deque`.

*po prawej stronie*\
Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** deque — obiekty nie są równe; **false** deque — obiekty są równe.

### <a name="remarks"></a>Uwagi

Porównanie deque — obiekty opiera się na parowania porównania ich elementów. Dwa deque — obiekty są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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
```

```Output
The deques are not equal.
```

## <a name="op_lt"></a> Operator&lt;

Sprawdza, czy obiekt deque, po lewej stronie operatora jest mniejszy niż obiekt deque — po prawej stronie.

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt typu `deque`.

*po prawej stronie*\
Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli deque po lewej stronie operatora jest mniejszy niż i nie równa deque — po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie deque — obiekty opiera się na parowania porównania ich elementów. Mniej-niż relacji między dwoma obiektami opiera się na porównanie pierwszy pary nierówne elementów.

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
```

```Output
Deque c1 is less than deque c2.
```

## <a name="op_lt_eq"></a> Operator&lt;=

Sprawdza, czy deque — obiekt po lewej stronie operatora jest mniejszy niż lub równy obiektowi deque — po prawej stronie.

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt typu `deque`.

*po prawej stronie*\
Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli deque po lewej stronie operatora jest mniejszy niż lub równa deque — po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie deque — obiekty opiera się na parowania porównania ich elementów. Mniejszą lub równą do relacji między dwoma obiektami opiera się na porównaniu pierwszy pary nierówne elementów.

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
```

```Output
Deque c1 is less than or equal to deque c2.
```

## <a name="op_eq_eq"></a> operator ==

Sprawdza, czy obiekt deque po lewej stronie operatora jest równy obiektowi deque — po prawej stronie.

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt typu `deque`.

*po prawej stronie*\
Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli deque po lewej stronie operatora jest równy deque — po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie deque — obiekty opiera się na parowania porównania ich elementów. Dwa deques są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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
```

```Output
The deques are equal.
The deques are not equal.
```

## <a name="op_gt"></a> Operator&gt;

Sprawdza, czy obiekt deque po lewej stronie operatora jest większy niż obiekt deque — po prawej stronie.

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt typu `deque`.

*po prawej stronie*\
Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli deque po lewej stronie operatora jest większy niż deque — po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie deque — obiekty opiera się na parowania porównania ich elementów. Większą-niż relacji między dwoma obiektami opiera się na porównanie pierwszy pary nierówne elementów.

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
```

```Output
Deque c1 is greater than deque c2.
```

## <a name="op_gt_eq"></a> Operator&gt;=

Sprawdza, czy obiekt deque po lewej stronie operatora jest większy lub równy obiektowi deque — po prawej stronie.

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt typu `deque`.

*po prawej stronie*\
Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli deque po lewej stronie operatora jest większy niż lub równa deque — po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie deque — obiekty opiera się na parowania porównania ich elementów. Większa lub równa relacji między dwoma obiektami opiera się na porównaniu pierwszy pary nierówne elementów.

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
```

```Output
Deque c1 is greater than or equal to deque c2.
```

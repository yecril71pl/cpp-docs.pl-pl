---
title: Operatory &lt;deque&gt;
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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883817"
---
# <a name="ltdequegt-operators"></a>Operatory &lt;deque&gt;

## <a name="op_neq"></a>operator! =

Testuje, czy obiekt deque po lewej stronie operatora nie jest równy obiektowi deque po prawej stronie.

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `deque`.

*prawa*\
Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli obiekty deque nie są równe; **wartość false** , jeśli obiekty deque są równe.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami deque jest oparte na porównaniu z przełączaniem ich elementów. Dwa obiekty deque są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

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

## <a name="op_lt"></a>&lt; operatora

Testuje, czy obiekt deque po lewej stronie operatora jest mniejszy niż obiekt deque po prawej stronie.

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `deque`.

*prawa*\
Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**true** , jeśli deque po lewej stronie operatora jest mniejszy niż i równy deque po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami deque jest oparte na porównaniu z przełączaniem ich elementów. Relacja mniejsza niż między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

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

## <a name="op_lt_eq"></a>&lt;operatora =

Testuje, czy obiekt deque po lewej stronie operatora jest mniejszy niż lub równy obiektowi deque po prawej stronie.

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `deque`.

*prawa*\
Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli deque po lewej stronie operatora jest mniejszy lub równy deque po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami deque jest oparte na porównaniu z przełączaniem ich elementów. Mniejsza lub równa relacji między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

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

## <a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt deque po lewej stronie operatora jest równy obiektowi deque po prawej stronie.

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `deque`.

*prawa*\
Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli deque po lewej stronie operatora jest równy deque po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami deque jest oparte na porównaniu z przełączaniem ich elementów. Dwa deques są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

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

## <a name="op_gt"></a>&gt; operatora

Testuje, czy obiekt deque po lewej stronie operatora jest większy niż obiekt deque po prawej stronie.

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `deque`.

*prawa*\
Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli deque po lewej stronie operatora jest większy od deque po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami deque jest oparte na porównaniu z przełączaniem ich elementów. Relacja większa niż między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

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

## <a name="op_gt_eq"></a>&gt;operatora =

Testuje, czy obiekt deque po lewej stronie operatora jest większy niż lub równy obiektowi deque po prawej stronie.

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `deque`.

*prawa*\
Obiekt typu `deque`.

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli deque po lewej stronie operatora jest większy lub równy deque po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami deque jest oparte na porównaniu z przełączaniem ich elementów. Większa lub równa relacji między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

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

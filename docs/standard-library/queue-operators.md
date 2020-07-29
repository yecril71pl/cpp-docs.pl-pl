---
title: '&lt;&gt;Operatory kolejki'
ms.date: 11/04/2016
f1_keywords:
- queue/std::operator!=
- queue/std::operator&gt;
- queue/std::operator&gt;=
- queue/std::operator&lt;
- queue/std::operator&lt;=
- queue/std::operator==
ms.assetid: 7c435b48-175c-45b0-88eb-24561044019c
helpviewer_keywords:
- std::operator!= (queue)
- std::operator&gt; (queue)
- std::operator&gt;= (queue)
- std::operator&lt; (queue)
- std::operator&lt;= (queue)
- std::operator== (queue)
ms.openlocfilehash: 8c02e79e6a300f23ac31ea876c9d4576cfe5e9a8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232927"
---
# <a name="ltqueuegt-operators"></a>&lt;&gt;Operatory kolejki

## <a name="operator"></a><a name="op_neq"></a>operator! =

Testuje, czy obiekt kolejki po lewej stronie operatora nie jest równy obiektowi kolejki po prawej stronie.

```cpp
bool operator!=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `queue`.

*Kliknij*\
Obiekt typu `queue`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli kolejki nie są równe; **`false`** Jeśli kolejki są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów Queue jest oparte na porównaniu z przełączaniem ich elementów. Dwie kolejki są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

### <a name="example"></a>Przykład

```cpp
// queue_op_ne.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a>zakład&lt;

Testuje, czy obiekt kolejki po lewej stronie operatora jest mniejszy niż obiekt kolejki po prawej stronie.

```cpp
bool operator<(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `queue`.

*Kliknij*\
Obiekt typu `queue`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli kolejka po lewej stronie operatora jest mniejsza niż i nie równa kolejki po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Porównanie obiektów Queue jest oparte na porównaniu z przełączaniem ich elementów. Relacja mniejsza niż między dwoma obiektami kolejki opiera się na porównaniu pierwszej pary nierównych elementów.

### <a name="example"></a>Przykład

```cpp
// queue_op_lt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 < q2 )
      cout << "The queue q1 is less than the queue q2." << endl;
   else
      cout << "The queue q1 is not less than the queue q2." << endl;

   if ( q1 < q3 )
      cout << "The queue q1 is less than the queue q3." << endl;
   else
      cout << "The queue q1 is not less than the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is not less than the queue q3.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>zakład&lt;=

Testuje, czy obiekt kolejki po lewej stronie operatora jest mniejszy niż lub równy obiektowi kolejki po prawej stronie.

```cpp
bool operator<=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `queue`.

*Kliknij*\
Obiekt typu `queue`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli kolejka po lewej stronie operatora jest ściśle mniejsza niż kolejka po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Porównanie obiektów Queue jest oparte na porównaniu z przełączaniem ich elementów. Mniejsza lub równa relacji między dwoma obiektami kolejki jest oparta na porównaniu pierwszej pary nierównych elementów.

### <a name="example"></a>Przykład

```cpp
// queue_op_le.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 5 );
   q1.push( 10 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 5 );
   q3.push( 10 );

   if ( q1 <= q2 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;

   if ( q1 <= q3 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is greater than the queue q2.
The queue q1 is less than or equal to the queue q3.
```

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt kolejki po lewej stronie operatora jest równy obiektowi kolejki po prawej stronie.

```cpp
bool operator==(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `queue`.

*Kliknij*\
Obiekt typu `queue`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli kolejki nie są równe; **`false`** Jeśli kolejki są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów Queue jest oparte na porównaniu z przełączaniem ich elementów. Dwie kolejki są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

### <a name="example"></a>Przykład

```cpp
// queue_op_eq.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a>zakład&gt;

Testuje, czy obiekt kolejki po lewej stronie operatora jest większy niż obiekt kolejki po prawej stronie.

```cpp
bool operator>(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `queue`.

*Kliknij*\
Obiekt typu `queue`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli kolejka po lewej stronie operatora jest ściśle mniejsza niż kolejka po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Porównanie obiektów Queue jest oparte na porównaniu z przełączaniem ich elementów. Relacja większa niż między dwoma obiektami kolejki opiera się na porównaniu pierwszej pary nierównych elementów.

### <a name="example"></a>Przykład

```cpp
// queue_op_gt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q1.push( 3 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 > q2 )
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q2." << endl;

   if ( q1> q3 )
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is not greater than the queue q2.
The queue q1 is greater than the queue q3.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>zakład&gt;=

Testuje, czy obiekt kolejki po lewej stronie operatora jest większy niż lub równy obiektowi kolejki po prawej stronie.

```cpp
bool operator>=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `queue`.

*Kliknij*\
Obiekt typu `queue`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli kolejka po lewej stronie operatora jest ściśle mniejsza niż kolejka po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Porównanie obiektów Queue jest oparte na porównaniu z przełączaniem ich elementów. Dwie kolejki są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

### <a name="example"></a>Przykład

```cpp
// queue_op_ge.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 >= q2 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q2." << endl;

   if ( q1>= q3 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is greater than or equal to the queue q3.
```

---
title: '&lt;kolejka&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- queue/std::operator!=
- queue/std::operator&gt;
- queue/std::operator&gt;=
- queue/std::operator&lt;
- queue/std::operator&lt;=
- queue/std::operator==
dev_langs:
- C++
ms.assetid: 7c435b48-175c-45b0-88eb-24561044019c
helpviewer_keywords:
- std::operator!= (queue)
- std::operator&gt; (queue)
- std::operator&gt;= (queue)
- std::operator&lt; (queue)
- std::operator&lt;= (queue)
- std::operator== (queue)
ms.openlocfilehash: d2d8efe00e5fc03e882086e3c7cfa5c0b7f3ee0c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101070"
---
# <a name="ltqueuegt-operators"></a>&lt;kolejka&gt; operatorów

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator! =

Sprawdza, czy obiekt kolejki po lewej stronie operatora nie jest taki sam jak obiekt kolejki po prawej stronie.

```cpp
bool operator!=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `queue`.

*right*<br/>
Obiekt typu `queue`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** kolejki nie są równe; **false** kolejki są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów kolejki jest oparty na parowania porównania ich elementów. Dwie kolejki są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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

## <a name="op_lt"></a>  Operator&lt;

Sprawdza, czy obiekt kolejki po lewej stronie operatora jest mniejszy niż obiekt kolejki po prawej stronie.

```cpp
bool operator<(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `queue`.

*right*<br/>
Obiekt typu `queue`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli kolejka po lewej stronie operatora jest mniejszy niż i nie równe do kolejki po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów kolejki jest oparty na parowania porównania ich elementów. Mniej-niż relacji między dwoma obiektami kolejki opiera się na porównanie pierwszy pary nierówne elementów.

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

## <a name="op_lt_eq"></a>  Operator&lt;=

Sprawdza, czy kolejka obiektu po lewej stronie operatora jest mniejszy niż lub równy obiektowi kolejki po prawej stronie.

```cpp
bool operator<=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `queue`.

*right*<br/>
Obiekt typu `queue`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli kolejki po lewej stronie operatora jest mniejsza niż kolejki po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów kolejki jest oparty na parowania porównania ich elementów. Mniejszą lub równą do relacji między obiektami kolejki dwa opiera się na porównanie pierwszy pary nierówne elementów.

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

## <a name="op_eq_eq"></a>  operator ==

Sprawdza, czy obiekt kolejki po lewej stronie operatora jest równy obiektowi kolejki po prawej stronie.

```cpp
bool operator==(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `queue`.

*right*<br/>
Obiekt typu `queue`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** kolejki nie są równe; **false** kolejki są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów kolejki jest oparty na parowania porównania ich elementów. Dwie kolejki są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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

## <a name="op_gt"></a>  Operator&gt;

Sprawdza, czy obiekt kolejki po lewej stronie operatora jest większy niż obiekt kolejki po prawej stronie.

```cpp
bool operator>(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `queue`.

*right*<br/>
Obiekt typu `queue`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli kolejki po lewej stronie operatora jest mniejsza niż kolejki po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów kolejki jest oparty na parowania porównania ich elementów. Większą-niż relacji między dwoma obiektami kolejki opiera się na porównanie pierwszy pary nierówne elementów.

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

## <a name="op_gt_eq"></a>  Operator&gt;=

Sprawdza, czy obiekt kolejki po lewej stronie operatora jest większy lub równy obiektowi kolejki po prawej stronie.

```cpp
bool operator>=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `queue`.

*right*<br/>
Obiekt typu `queue`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli kolejki po lewej stronie operatora jest mniejsza niż kolejki po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów kolejki jest oparty na parowania porównania ich elementów. Dwie kolejki są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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

## <a name="see-also"></a>Zobacz także

[\<queue>](../standard-library/queue.md)<br/>

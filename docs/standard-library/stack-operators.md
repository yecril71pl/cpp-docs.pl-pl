---
title: '&lt;stos&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- stack/std::operator!=
- stack/std::operator&gt;
- stack/std::operator&gt;=
- stack/std::operator&lt;
- stack/std::operator&lt;=
- stack/std::operator==
dev_langs:
- C++
ms.assetid: 9c1fc282-2f61-4727-9e80-84ea5d4934a2
helpviewer_keywords:
- std::operator!= (stack)
- std::operator&gt; (stack)
- std::operator&gt;= (stack)
- std::operator&lt; (stack)
- std::operator&lt;= (stack)
- std::operator== (stack)
ms.openlocfilehash: 5d3bafd2d3112a2f4155f55a554b6c9c2e351b1f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltstackgt-operators"></a>&lt;stos&gt; operatory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator! =

Testy, jeśli obiekt stosu po lewej stronie operatora nie jest równa stosu obiektów po prawej stronie.

```cpp
bool operator!=(const stack <Type, Container>& left, const stack <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **stosu**.

`right` Obiekt typu **stosu**.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** stosów lub stosy nie są równe; **false** stosów lub stosy są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów stosy opiera się na parowania porównanie ich elementów. Stosy dwóch są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

### <a name="example"></a>Przykład

```cpp
// stack_op_me.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with vector base containers
   stack <int, vector<int> > s1, s2, s3;

   // The following would have cause an error because stacks with
   // different base containers are not equality comparable
   // stack <int, list<int> >  s3;

   s1.push( 1 );
   s2.push( 2 );
   s3.push( 1 );

   if ( s1 != s2 )
      cout << "The stacks s1 and s2 are not equal." << endl;
   else
      cout << "The stacks s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The stacks s1 and s3 are not equal." << endl;
   else
      cout << "The stacks s1 and s3 are equal." << endl;
}
```

```Output
The stacks s1 and s2 are not equal.
The stacks s1 and s3 are equal.
```

## <a name="op_lt"></a>  Operator&lt;

Testy, jeśli obiekt stosu po lewej stronie operatora jest mniejsza niż obiekt stosu po prawej stronie.

```cpp
bool operator<(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **stosu**.

`right` Obiekt typu **stosu**.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli stosu po lewej stronie operatora jest mniejsza niż i nie równa stosu po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów stosu jest oparta na parowania porównanie ich elementów. Less — niż relacji między dwoma obiektami stosu jest oparta na porównanie pierwszego pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// stack_op_lt.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 2 );
   s1.push( 4 );
   s1.push( 6 );
   s1.push( 8 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 2 );
   s3.push( 4 );
   s3.push( 6 );
   s3.push( 8 );

   if ( s1 >= s2 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s2." << endl;

   if ( s1>= s3 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s3." << endl;

   // to print out the stack s1 ( by unstacking the elements):
   stack <int>::size_type i_size_s1 = s1.size( );
   cout << "The stack s1 from the top down is: ( ";
   unsigned int i;
   for ( i = 1 ; i <= i_size_s1 ; i++ )
   {
      cout << s1.top( ) << " ";
      s1.pop( );
   }
   cout << ")." << endl;
}
```

```Output
The stack s1 is less than the stack s2.
The stack s1 is greater than or equal to the stack s3.
The stack s1 from the top down is: ( 8 6 4 2 ).
```

## <a name="op_lt_eq"></a>  Operator&lt;=

Testy, jeśli obiekt stosu po lewej stronie operatora jest mniejsza niż lub równe obiekcie stosu po prawej stronie.

```cpp
bool operator<=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **stosu**.

`right` Obiekt typu **stosu**.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli stosu po lewej stronie operatora jest mniejsza niż lub równa stosu po prawej stronie operatora, w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów stosu jest oparta na parowania porównanie ich elementów. Mniej niż lub równe relacji między dwoma obiektami stosu jest oparta na porównanie pierwszego pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// stack_op_le.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with default deque base container
   stack <int> s1, s2, s3;

   s1.push( 5 );
   s1.push( 10 );
   s2.push( 1 );
   s2.push( 2 );
   s3.push( 5 );
   s3.push( 10 );

   if ( s1 <= s2 )
      cout << "The stack s1 is less than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is greater than "
           << "the stack s2." << endl;

   if ( s1 <= s3 )
      cout << "The stack s1 is less than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is greater than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is greater than the stack s2.
The stack s1 is less than or equal to the stack s3.
```

## <a name="op_eq_eq"></a>  operator ==

Testy, jeśli obiekt stosu po lewej stronie operatora jest taki sam obiekt stosu po prawej stronie.

```cpp
bool operator==(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **stosu**.

`right` Obiekt typu **stosu**.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** stosów lub stosy są równe; **false** stosów lub stosy nie są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów stosu jest oparta na parowania porównanie ich elementów. Stosy dwóch są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

### <a name="example"></a>Przykład

```cpp
// stack_op_eq.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with vector base containers
   stack <int, vector<int> > s1, s2, s3;

   // The following would have cause an error because stacks with
   // different base containers are not equality comparable
   // stack <int, list<int> > s3;

   s1.push( 1 );
   s2.push( 2 );
   s3.push( 1 );

   if ( s1 == s2 )
      cout << "The stacks s1 and s2 are equal." << endl;
   else
      cout << "The stacks s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The stacks s1 and s3 are equal." << endl;
   else
      cout << "The stacks s1 and s3 are not equal." << endl;
}
```

```Output
The stacks s1 and s2 are not equal.
The stacks s1 and s3 are equal.
```

## <a name="op_gt"></a>  Operator&gt;

Testy, jeśli obiekt stosu po lewej stronie operatora jest większy niż obiekt stosu po prawej stronie.

```cpp
bool operator>(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **stosu**.

`right` Obiekt typu **stosu**.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli stosu po lewej stronie operatora jest większa niż i nie równa stosu po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów stosu jest oparta na parowania porównanie ich elementów. Większa-niż relacji między dwoma obiektami stosu jest oparta na porównanie pierwszego pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// stack_op_gt.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 1 );
   s1.push( 2 );
   s1.push( 3 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 1 );
   s3.push( 2 );

   if ( s1 > s2 )
      cout << "The stack s1 is greater than "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is not greater than "
           << "the stack s2." << endl;

   if ( s1> s3 )
      cout << "The stack s1 is greater than "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is not greater than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is not greater than the stack s2.
The stack s1 is greater than the stack s3.
```

## <a name="op_gt_eq"></a>  Operator&gt;=

Testy, jeśli obiekt stosu po lewej stronie operatora jest większa niż lub równa obiekcie stosu po prawej stronie.

```cpp
bool operator>=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu **stosu**.

`right` Obiekt typu **stosu**.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli stos po lewej stronie operatora jest ściśle mniejsza niż stos po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów stosu jest oparta na parowania porównanie ich elementów. Większa niż lub równa relacji między obiektami dwóch stosu opiera się na porównanie pierwszego pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// stack_op_ge.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 1 );
   s1.push( 2 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 1 );
   s3.push( 2 );

   if ( s1 >= s2 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s2." << endl;

   if ( s1>= s3 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is less than the stack s2.
The stack s1 is greater than or equal to the stack s3.
```

## <a name="see-also"></a>Zobacz także

[\<stack>](../standard-library/stack.md)<br/>

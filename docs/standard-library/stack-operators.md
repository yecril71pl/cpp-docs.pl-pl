---
title: Operatory&gt; stosu &lt;
ms.date: 11/04/2016
f1_keywords:
- stack/std::operator!=
- stack/std::operator&gt;
- stack/std::operator&gt;=
- stack/std::operator&lt;
- stack/std::operator&lt;=
- stack/std::operator==
ms.assetid: 9c1fc282-2f61-4727-9e80-84ea5d4934a2
helpviewer_keywords:
- std::operator!= (stack)
- std::operator&gt; (stack)
- std::operator&gt;= (stack)
- std::operator&lt; (stack)
- std::operator&lt;= (stack)
- std::operator== (stack)
ms.openlocfilehash: 169698d30edd4a7995cb05e1909c1ffc38b0b6ef
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419435"
---
# <a name="ltstackgt-operators"></a>Operatory&gt; stosu &lt;

## <a name="op_neq"></a>operator! =

Testuje, czy obiekt stosu po lewej stronie operatora nie jest równy obiektowi stosu po prawej stronie.

```cpp
bool operator!=(const stack <Type, Container>& left, const stack <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `stack`.

*prawa*\
Obiekt typu `stack`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli stosy lub stosy nie są równe; **Fałsz** , jeśli stosy lub stosy są równe.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami Stacks opiera się na porównaniu z przełączaniem ich elementów. Dwa stosy są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

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

## <a name="op_lt"></a>&lt; operatora

Testuje, czy obiekt stosu po lewej stronie operatora jest mniejszy niż obiekt stosu po prawej stronie.

```cpp
bool operator<(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `stack`.

*prawa*\
Obiekt typu `stack`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli stos po lewej stronie operatora jest mniejszy od i nie jest równy stosowi po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów stosu jest oparte na porównaniu z przełączaniem ich elementów. Relacja mniejsza niż między dwoma obiektami stosu opiera się na porównaniu pierwszej pary nierównych elementów.

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

## <a name="op_lt_eq"></a>&lt;operatora =

Testuje, czy obiekt stosu po lewej stronie operatora jest mniejszy niż lub równy obiektowi stosu po prawej stronie.

```cpp
bool operator<=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `stack`.

*prawa*\
Obiekt typu `stack`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli stos po lewej stronie operatora jest mniejszy lub równy stosowi po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów stosu jest oparte na porównaniu z przełączaniem ich elementów. Mniejsza lub równa relacji między dwoma obiektami stosu bazuje na porównaniu pierwszej pary nierównych elementów.

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

## <a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt stosu po lewej stronie operatora jest równy obiektowi stosu po prawej stronie.

```cpp
bool operator==(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `stack`.

*prawa*\
Obiekt typu `stack`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli stosy lub stosy są równe; **Fałsz** , jeśli stosy lub stosy nie są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów stosu jest oparte na porównaniu z przełączaniem ich elementów. Dwa stosy są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

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

## <a name="op_gt"></a>&gt; operatora

Testuje, czy obiekt stosu po lewej stronie operatora jest większy niż obiekt stosu po prawej stronie.

```cpp
bool operator>(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `stack`.

*prawa*\
Obiekt typu `stack`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli stos po lewej stronie operatora jest większy niż i nie jest równy stosowi po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów stosu jest oparte na porównaniu z przełączaniem ich elementów. Relacja większa niż między dwoma obiektami stosu bazuje na porównaniu pierwszej pary nierównych elementów.

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

## <a name="op_gt_eq"></a>&gt;operatora =

Testuje, czy obiekt stosu po lewej stronie operatora jest większy niż lub równy obiektowi stosu po prawej stronie.

```cpp
bool operator>=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `stack`.

*prawa*\
Obiekt typu `stack`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli stos po lewej stronie operatora jest ściśle mniejszy niż stos po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów stosu jest oparte na porównaniu z przełączaniem ich elementów. Relacja większa niż lub równa relacji między dwoma obiektami stosu bazuje na porównaniu pierwszej pary nierównych elementów.

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

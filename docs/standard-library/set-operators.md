---
title: '&lt;ustawić operatory&gt;'
ms.date: 03/27/2019
f1_keywords:
- set/std::operator!=
- set/std::operator&gt;
- set/std::operator&gt;=
- set/std::operator&lt;
- set/std::operator&lt;=
- set/std::operator==
ms.assetid: b4256ebc-c449-4688-95db-fced42d20d4d
helpviewer_keywords:
- std::operator!= (set)
- std::operator&gt; (set)
- std::operator&gt;= (set)
- std::operator&lt; (set)
- std::operator&lt;= (set)
- std::operator== (set)
ms.openlocfilehash: 4618030cf81f79a085e16052c8b9c547201e3577
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875773"
---
# <a name="ltsetgt-operators"></a>&lt;ustawić operatory&gt;

## <a name="op_neq"></a>operator! = (Set)

Testuje, czy obiekt Set po lewej stronie operatora nie jest równy obiektowi Set po prawej stronie.

```cpp
bool operator!=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `set`.

*prawa*\
Obiekt typu `set`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli zestawy nie są równe; **wartość false** , jeśli zestawy są równe.

### <a name="remarks"></a>Uwagi

Porównanie między zestawami obiektów jest oparte na porównaniu z przełączaniem między swoimi elementami. Dwa zestawy są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

### <a name="example"></a>Przykład

```cpp
// set_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The sets s1 and s2 are not equal." << endl;
   else
      cout << "The sets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The sets s1 and s3 are not equal." << endl;
   else
      cout << "The sets s1 and s3 are equal." << endl;
}
/* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*/
```

## <a name="op_lt"></a>&lt; operatora (Set)

Testuje, czy obiekt Set po lewej stronie operatora jest mniejszy od obiektu Set po prawej stronie.

```cpp
bool operator<(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `set`.

*prawa*\
Obiekt typu `set`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli zestaw po lewej stronie operatora jest ściśle mniejszy niż zestaw po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między zestawami obiektów jest oparte na porównaniu z przełączaniem ich elementów. Relacja mniejsza niż między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

### <a name="example"></a>Przykład

```cpp
// set_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The set s1 is less than the set s2." << endl;
   else
      cout << "The set s1 is not less than the set s2." << endl;

   if ( s1 < s3 )
      cout << "The set s1 is less than the set s3." << endl;
   else
      cout << "The set s1 is not less than the set s3." << endl;
}
/* Output:
The set s1 is less than the set s2.
The set s1 is not less than the set s3.
*/
```

## <a name="op_lt_eq"></a>&lt;operatora = (Set)

Testuje, czy obiekt Set po lewej stronie operatora jest mniejszy od lub równy obiektowi Set po prawej stronie.

```cpp
bool operator!<=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `set`.

*prawa*\
Obiekt typu `set`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli zestaw po lewej stronie operatora jest mniejszy lub równy zestawowi po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między zestawami obiektów jest oparte na porównaniu z przełączaniem ich elementów. Mniejsza lub równa relacji między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

### <a name="example"></a>Przykład

```cpp
// set_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "Set s1 is less than or equal to the set s2." << endl;
   else
      cout << "The set s1 is greater than the set s2." << endl;

   if ( s1 <= s3 )
      cout << "Set s1 is less than or equal to the set s3." << endl;
   else
      cout << "The set s1 is greater than the set s3." << endl;

   if ( s1 <= s4 )
      cout << "Set s1 is less than or equal to the set s4." << endl;
   else
      cout << "The set s1 is greater than the set s4." << endl;
}
```

```Output
Set s1 is less than or equal to the set s2.
The set s1 is greater than the set s3.
Set s1 is less than or equal to the set s4.
```

## <a name="op_eq_eq"></a>operator = = (Set)

Testuje, czy obiekt Set po lewej stronie operatora jest równy obiektowi Set po prawej stronie.

```cpp
bool operator!==(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `set`.

*prawa*\
Obiekt typu `set`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli zestaw po lewej stronie operatora jest równy zestawowi po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między zestawami obiektów jest oparte na porównaniu z przełączaniem ich elementów. Dwa zestawy są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

### <a name="example"></a>Przykład

```cpp
// set_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The sets s1 and s2 are equal." << endl;
   else
      cout << "The sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The sets s1 and s3 are equal." << endl;
   else
      cout << "The sets s1 and s3 are not equal." << endl;
}
```

```Output
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
```

## <a name="op_gt"></a>&gt; operatora (Set)

Testuje, czy obiekt Set po lewej stronie operatora jest większy niż obiekt ustawiony po prawej stronie.

```cpp
bool operator>(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `set`.

*prawa*\
Obiekt typu `set`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli zestaw po lewej stronie operatora jest większy niż zestaw po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między zestawami obiektów jest oparte na porównaniu z przełączaniem ich elementów. Relacja większa niż między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

### <a name="example"></a>Przykład

```cpp
// set_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The set s1 is greater than the set s2." << endl;
   else
      cout << "The set s1 is not greater than the set s2." << endl;

   if ( s1 > s3 )
      cout << "The set s1 is greater than the set s3." << endl;
   else
      cout << "The set s1 is not greater than the set s3." << endl;
}
/* Output:
The set s1 is not greater than the set s2.
The set s1 is greater than the set s3.
*/
```

## <a name="op_gt_eq"></a>&gt;operatora = (Set)

Testuje, czy obiekt Set po lewej stronie operatora jest większy niż lub równy obiektowi Set po prawej stronie.

```cpp
bool operator!>=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `set`.

*prawa*\
Obiekt typu `set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli zestaw po lewej stronie operatora jest większy lub równy zestawowi po prawej stronie listy; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między zestawami obiektów jest oparte na porównaniu z przełączaniem ich elementów. Większa lub równa relacji między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

### <a name="example"></a>Przykład

```cpp
// set_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "Set s1 is greater than or equal to set s2." << endl;
   else
      cout << "The set s1 is less than the set s2." << endl;

   if ( s1 >= s3 )
      cout << "Set s1 is greater than or equal to set s3." << endl;
   else
      cout << "The set s1 is less than the set s3." << endl;

   if ( s1 >= s4 )
      cout << "Set s1 is greater than or equal to set s4." << endl;
   else
      cout << "The set s1 is less than the set s4." << endl;
}
```

```Output
The set s1 is less than the set s2.
Set s1 is greater than or equal to set s3.
Set s1 is greater than or equal to set s4.
```

## <a name="op_neq_multiset"></a>operator! = (zestaw wielokrotny)

Testuje, czy obiekt zestawu wielokrotnego po lewej stronie operatora nie jest równy obiektowi wielokrotnemu po prawej stronie.

```cpp
bool operator!=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `multiset`.

*prawa*\
Obiekt typu `multiset`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli zestawy lub zestawy wielozbiorowe nie są równe; **wartość false** , jeśli zestawy lub zestawy wielozbiorowe są równe.

### <a name="remarks"></a>Uwagi

Porównywanie obiektów zestawu wielokrotnego opiera się na porównaniu z przełączaniem między swoimi elementami. Dwa zestawy lub zestawy wielozbiorowe są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

### <a name="example"></a>Przykład

```cpp
// multiset_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The multisets s1 and s2 are not equal." << endl;
   else
      cout << "The multisets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The multisets s1 and s3 are not equal." << endl;
   else
      cout << "The multisets s1 and s3 are equal." << endl;
}
```

```Output
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
```

## <a name="op_lt_multiset"></a>&lt; operatora (zestaw wielokrotny)

Testuje, czy obiekt zestawu wielokrotnego po lewej stronie operatora jest mniejszy niż obiekt zestawu wielokrotnego po prawej stronie.

```cpp
bool operator<(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `multiset`.

*prawa*\
Obiekt typu `multiset`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli zestaw wielokrotny po lewej stronie operatora jest ściśle mniejszy niż zestaw wielokrotny po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównywanie obiektów zestawu wielokrotnego jest oparte na porównaniu z przełączaniem ich elementów. Relacja mniejsza niż między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

### <a name="example"></a>Przykład

```cpp
// multiset_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s2." << endl;

   if ( s1 < s3 )
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s3." << endl;
}
```

```Output
The multiset s1 is less than the multiset s2.
The multiset s1 is not less than the multiset s3.
```

## <a name="op_lt_eq_multiset"></a>operator&lt;= (zestaw wielokrotny)

Testuje, czy obiekt zestawu wielokrotnego po lewej stronie operatora jest mniejszy niż lub równy obiektowi zestawu wielokrotnego po prawej stronie.

```cpp
bool operator!<=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `multiset`.

*prawa*\
Obiekt typu `multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli zestaw wielokrotny po lewej stronie operatora jest mniejszy lub równy zestawowi wielokrotnemu po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównywanie obiektów zestawu wielokrotnego jest oparte na porównaniu z przełączaniem ich elementów. Mniejsza lub równa relacji między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

### <a name="example"></a>Przykład

```cpp
// multiset_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;

   if ( s1 <= s3 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;

   if ( s1 <= s4 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s4." << endl;
}
```

```Output
The multiset s1 is less than or equal to the multiset s2.
The multiset s1 is greater than the multiset s3.
The multiset s1 is less than or equal to the multiset s4.
```

## <a name="op_eq_eq_multiset"></a>operator = = (zestaw wielokrotny)

Testuje, czy obiekt zestawu wielokrotnego po lewej stronie operatora jest równy obiektowi zestaw wielokrotny po prawej stronie.

```cpp
bool operator!==(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `multiset`.

*prawa*\
Obiekt typu `multiset`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli zestaw wielokrotny po lewej stronie operatora jest równy zestawowi wielokrotnemu po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównywanie obiektów zestawu wielokrotnego jest oparte na porównaniu z przełączaniem ich elementów. Dwa zestawy lub zestawy wielozbiorowe są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

### <a name="example"></a>Przykład

```cpp
// multiset_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The multisets s1 and s2 are equal." << endl;
   else
      cout << "The multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The multisets s1 and s3 are equal." << endl;
   else
      cout << "The multisets s1 and s3 are not equal." << endl;
}
```

```Output
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
```

## <a name="op_gt_multiset"></a>&gt; operatora (zestaw wielokrotny)

Testuje, czy obiekt zestawu wielokrotnego po lewej stronie operatora jest większy niż obiekt zestawu wielokrotnego po prawej stronie.

```cpp
bool operator>(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `multiset`.

*prawa*\
Obiekt typu `multiset`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli zestaw wielokrotny po lewej stronie operatora jest większy niż zestaw wielokrotny po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównywanie obiektów zestawu wielokrotnego jest oparte na porównaniu z przełączaniem ich elementów. Relacja większa niż między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

### <a name="example"></a>Przykład

```cpp
// multiset_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not greater "
           << "than the multiset s2." << endl;

   if ( s1 > s3 )
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not greater than "
           << "the multiset s3." << endl;
}
```

```Output
The multiset s1 is not greater than the multiset s2.
The multiset s1 is greater than the multiset s3.
```

## <a name="op_gt_eq_multiset"></a>operator&gt;= (zestaw wielokrotny)

Testuje, czy obiekt zestawu wielokrotnego po lewej stronie operatora jest większy niż lub równy obiektowi zestaw wielokrotny po prawej stronie.

```cpp
bool operator!>=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `multiset`.

*prawa*\
Obiekt typu `multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli zestaw wielokrotny po lewej stronie operatora jest większy lub równy zestawowi wielokrotnemu po prawej stronie listy; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównywanie obiektów zestawu wielokrotnego jest oparte na porównaniu z przełączaniem ich elementów. Większa lub równa relacji między dwoma obiektami opiera się na porównaniu pierwszej pary nierównych elementów.

### <a name="example"></a>Przykład

```cpp
// multiset_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;

   if ( s1 >= s3 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;

   if ( s1 >= s4 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s4." << endl;
}
```

```Output
The multiset s1 is less than the multiset s2.
The multiset s1 is greater than or equal to the multiset s3.
The multiset s1 is greater than or equal to the multiset s4.
```

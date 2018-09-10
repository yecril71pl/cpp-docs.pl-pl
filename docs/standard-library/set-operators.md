---
title: '&lt;Ustaw&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- set/std::operator!=
- set/std::operator&gt;
- set/std::operator&gt;=
- set/std::operator&lt;
- set/std::operator&lt;=
- set/std::operator==
dev_langs:
- C++
ms.assetid: b4256ebc-c449-4688-95db-fced42d20d4d
helpviewer_keywords:
- std::operator!= (set)
- std::operator&gt; (set)
- std::operator&gt;= (set)
- std::operator&lt; (set)
- std::operator&lt;= (set)
- std::operator== (set)
ms.openlocfilehash: 43ee5b62bcda9a38946bfd61c3ed3efbc8d89523
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110074"
---
# <a name="ltsetgt-operators"></a>&lt;Ustaw&gt; operatorów

||||
|-|-|-|
|[Operator! = (set)](#op_neq)|[operator&gt; (ustawiona)](#op_gt)|[operator&gt;= (set)](#eq)|
|[operator&lt; (ustawiona)](#op_lt)|[operator&lt;= (set)](#eq)|[Operator == (set)](#op_eq_eq)|
|[Operator! = (multiset)](#op_neq_multiset)|[operator&gt; (multiset)](#op_gt_multiset)|[operator&gt;= (multiset)](#op_gt_eq_multiset)|
|[operator&lt; (multiset)](#op_lt_multiset)|[operator&lt;= (multiset)](#op_lt_eq_multiset)|[Operator == (multiset)](#op_eq_eq_multiset)|

## <a name="op_neq"></a>  Operator! = (set)

Sprawdza, czy obiekt zestawu po lewej stronie operatora nie jest równy obiektowi zestaw po prawej stronie.

```cpp
bool operator!=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `set`.

*right*<br/>
Obiekt typu `set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** zestawy nie są równe; **false** zestawy są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów zbioru opiera się na parowania porównanie ich elementów. Dwa zestawy są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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
\* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*\
```

## <a name="op_lt"></a>  operator&lt; (ustawiona)

Sprawdza, czy obiekt zestawu, po lewej stronie operatora jest mniejszy niż obiekt zestawu po prawej stronie.

```cpp
bool operator<(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `set`.

*right*<br/>
Obiekt typu `set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli zestaw po lewej stronie operatora jest mniejsza niż zestaw po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów zbioru opiera się na parowania porównania ich elementów. Mniej-niż relacji między dwoma obiektami opiera się na porównanie pierwszy pary nierówne elementów.

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
\* Output:
The set s1 is less than the set s2.
The set s1 is not less than the set s3.
*\
```

## <a name="op_lt_eq"></a>  operator&lt;= (set)

Sprawdza, czy zestaw obiektów po lewej stronie operatora jest mniejszy niż lub równy obiektowi zestaw po prawej stronie.

```cpp
bool operator!<=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `set`.

*right*<br/>
Obiekt typu `set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli zestaw po lewej stronie operatora jest mniejszy niż lub równe do zestawu po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów zbioru opiera się na parowania porównania ich elementów. Mniejszą lub równą do relacji między dwoma obiektami opiera się na porównaniu pierwszy pary nierówne elementów.

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
\* Output:
Set s1 is less than or equal to the set s2.
The set s1 is greater than the set s3.
Set s1 is less than or equal to the set s4.
*\
```

## <a name="op_eq_eq"></a>  Operator == (set)

Sprawdza, czy obiekt zestawu po lewej stronie operatora jest równy obiektowi zestaw po prawej stronie.

```cpp
bool operator!==(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `set`.

*right*<br/>
Obiekt typu `set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli zestaw po lewej stronie operatora jest równy zestaw po prawej stronie operatora, a w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów zbioru opiera się na parowania porównania ich elementów. Dwa zestawy są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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
\* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*\
```

## <a name="op_gt"></a>  operator&gt; (ustawiona)

Sprawdza, czy obiekt zestawu po lewej stronie operatora jest większy niż obiekt zestawu po prawej stronie.

```cpp
bool operator>(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `set`.

*right*<br/>
Obiekt typu `set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli zestaw po lewej stronie operatora jest większy niż zestaw po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów zbioru opiera się na parowania porównania ich elementów. Większą-niż relacji między dwoma obiektami opiera się na porównanie pierwszy pary nierówne elementów.

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
\* Output:
The set s1 is not greater than the set s2.
The set s1 is greater than the set s3.
*\
```

## <a name="op_gt_eq"></a>  operator&gt;= (set)

Sprawdza, czy obiekt zestawu po lewej stronie operatora jest większy lub równy obiektowi zestaw po prawej stronie.

```cpp
bool operator!>=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `set`.

*right*<br/>
Obiekt typu `set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli zestaw po lewej stronie operatora jest większy niż lub równe do zestawu po prawej stronie listy; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów zbioru opiera się na parowania porównania ich elementów. Większa lub równa relacji między dwoma obiektami opiera się na porównaniu pierwszy pary nierówne elementów.

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
\* Output:
The set s1 is less than the set s2.
Set s1 is greater than or equal to set s3.
Set s1 is greater than or equal to set s4.
*\
```

## <a name="op_neq_multiset"></a>  Operator! = (multiset)

Sprawdza, czy obiekt multiset — po lewej stronie operatora nie jest równy obiektowi multiset — po prawej stronie.

```cpp
bool operator!=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `multiset`.

*right*<br/>
Obiekt typu `multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** zestawy lub multisets nie są równe; **false** zestawy lub multisets są równe.

### <a name="remarks"></a>Uwagi

Porównanie multiset — obiekty opiera się na parowania porównanie ich elementów. Dwa zestawy lub multisets są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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
\* Output:
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
*\
```

## <a name="op_lt_multiset"></a>  operator&lt; (multiset)

Sprawdza, czy multiset — obiekt po lewej stronie operatora jest mniejszy niż obiekt multiset — po prawej stronie.

```cpp
bool operator<(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `multiset`.

*right*<br/>
Obiekt typu `multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli multiset po lewej stronie operatora jest mniejsza niż multiset po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie multiset — obiekty opiera się na parowania porównania ich elementów. Mniej-niż relacji między dwoma obiektami opiera się na porównanie pierwszy pary nierówne elementów.

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
\* Output:
The multiset s1 is less than the multiset s2.
The multiset s1 is not less than the multiset s3.
*\
```

## <a name="op_lt_eq_multiset"></a>  operator&lt;= (multiset)

Sprawdza, czy zestaw wielokrotny obiektu po lewej stronie operatora jest mniejszy niż lub równy obiektowi multiset — po prawej stronie.

```cpp
bool operator!<=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `multiset`.

*right*<br/>
Obiekt typu `multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli multiset po lewej stronie operatora jest mniejszy niż lub równa multiset po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie multiset — obiekty opiera się na parowania porównania ich elementów. Mniejszą lub równą do relacji między dwoma obiektami opiera się na porównaniu pierwszy pary nierówne elementów.

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
\* Output:
The multiset s1 is less than or equal to the multiset s2.
The multiset s1 is greater than the multiset s3.
The multiset s1 is less than or equal to the multiset s4.
*\
```

## <a name="op_eq_eq_multiset"></a>  Operator == (multiset)

Sprawdza, czy multiset — obiekt po lewej stronie operatora jest równy obiektowi multiset — po prawej stronie.

```cpp
bool operator!==(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `multiset`.

*right*<br/>
Obiekt typu `multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli multiset po lewej stronie operatora jest równy multiset po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie multiset — obiekty opiera się na parowania porównania ich elementów. Dwa zestawy lub multisets są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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
\* Output:
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
*\
```

## <a name="op_gt_multiset"></a>  operator&gt; (multiset)

Sprawdza, czy multiset — obiekt po lewej stronie operatora jest większy niż obiekt multiset — po prawej stronie.

```cpp
bool operator>(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `multiset`.

*right*<br/>
Obiekt typu `multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli multiset po lewej stronie operatora jest większy niż multiset po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie multiset — obiekty opiera się na parowania porównania ich elementów. Większą-niż relacji między dwoma obiektami opiera się na porównanie pierwszy pary nierówne elementów.

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
\* Output:
The multiset s1 is not greater than the multiset s2.
The multiset s1 is greater than the multiset s3.
*\
```

## <a name="op_gt_eq_multiset"></a>  operator&gt;= (multiset)

Sprawdza, czy multiset — obiekt po lewej stronie operatora jest większy lub równy obiektowi multiset — po prawej stronie.

```cpp
bool operator!>=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `multiset`.

*right*<br/>
Obiekt typu `multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli multiset po lewej stronie operatora jest większy niż lub równa multiset po prawej stronie listy; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie multiset — obiekty opiera się na parowania porównania ich elementów. Większa lub równa relacji między dwoma obiektami opiera się na porównaniu pierwszy pary nierówne elementów.

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
\* Output:
The multiset s1 is less than the multiset s2.
The multiset s1 is greater than or equal to the multiset s3.
The multiset s1 is greater than or equal to the multiset s4.
*\
```

## <a name="see-also"></a>Zobacz także

[\<Ustaw >](../standard-library/set.md)<br/>

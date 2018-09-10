---
title: '&lt;Mapa&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- map/std::operator!=
- map/std::operator&gt;
- map/std::operator&gt;=
- map/std::operator&lt;
- map/std::operator&lt;=
- map/std::operator==
dev_langs:
- C++
ms.assetid: 7df02b9f-701c-44ed-834a-a819badc5bd0
helpviewer_keywords:
- std::operator!= (map)
- std::operator&gt; (map)
- std::operator&gt;= (map)
- std::operator&lt; (map)
- std::operator&lt;= (map)
- std::operator== (map)
ms.openlocfilehash: 0113f792a20c1680ce931d43cbaf016e7bcfaf59
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108309"
---
# <a name="ltmapgt-operators"></a>&lt;Mapa&gt; operatorów

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|
|[Operator! = (multimap)](#op_neq_multimap)|[Operator&gt;](#op_gt_multimap)|[Operator&gt;=](#op_gt_eq_multimap)|
|[Operator&lt;](#op_lt_multimap)|[Operator&lt;=](#op_lt_eq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="op_neq"></a>  operator! =

Sprawdza, czy obiekt mapy po lewej stronie operatora nie jest równy obiektowi mapy po prawej stronie.

```cpp
bool operator!=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `map`.

*right*<br/>
Obiekt typu `map`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** mapy nie są równe; **false** mapy są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów mapy opiera się na parowania porównania ich elementów. Dwie mapy są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

### <a name="example"></a>Przykład

```cpp
// map_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The maps m1 and m2 are not equal." << endl;
   else
      cout << "The maps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The maps m1 and m3 are not equal." << endl;
   else
      cout << "The maps m1 and m3 are equal." << endl;
}
\* Output:
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
*\
```

## <a name="op_lt"></a>  Operator&lt;

Sprawdza, czy obiektu mapy po lewej stronie operatora jest mniejszy niż obiekt mapy po prawej stronie.

```cpp
bool operator<(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `map`.

*right*<br/>
Obiekt typu `map`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli mapa po lewej stronie operatora jest mniejsza niż mapy po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów mapy opiera się na parowania porównania ich elementów. Mniej-niż relacji między dwoma obiektami opiera się na porównanie pierwszy pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// map_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The map m1 is less than the map m2." << endl;
   else
      cout << "The map m1 is not less than the map m2." << endl;

   if ( m1 < m3 )
      cout << "The map m1 is less than the map m3." << endl;
   else
      cout << "The map m1 is not less than the map m3." << endl;
}
\* Output:
The map m1 is less than the map m2.
The map m1 is not less than the map m3.
*\
```

## <a name="op_lt_eq"></a>  Operator&lt;=

Sprawdza, czy mapa obiektu po lewej stronie operatora jest mniejszy niż lub równy obiektowi mapy po prawej stronie.

```cpp
bool operator<=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `map`.

*right*<br/>
Obiekt typu `map`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli mapa po lewej stronie operatora jest mniejszy niż lub równe do mapy po prawej stronie operatora; w przeciwnym **false**.

### <a name="example"></a>Przykład

```cpp
// map_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "The map m1 is less than or equal to the map m2." << endl;
   else
      cout << "The map m1 is greater than the map m2." << endl;

   if ( m1 <= m3 )
      cout << "The map m1 is less than or equal to the map m3." << endl;
   else
      cout << "The map m1 is greater than the map m3." << endl;

   if ( m1 <= m4 )
      cout << "The map m1 is less than or equal to the map m4." << endl;
   else
      cout << "The map m1 is greater than the map m4." << endl;
}
\* Output:
The map m1 is less than or equal to the map m2.
The map m1 is greater than the map m3.
The map m1 is less than or equal to the map m4.
*\
```

## <a name="op_eq_eq"></a>  operator ==

Sprawdza, czy obiekt mapy po lewej stronie operatora jest równy obiektowi mapy po prawej stronie.

```cpp
bool operator==(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `map`.

*right*<br/>
Obiekt typu `map`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli mapa po lewej stronie operatora jest równy mapy po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów mapy opiera się na parowania porównania ich elementów. Dwie mapy są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

### <a name="example"></a>Przykład

```cpp
// map_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 == m2 )
      cout << "The maps m1 and m2 are equal." << endl;
   else
      cout << "The maps m1 and m2 are not equal." << endl;

   if ( m1 == m3 )
      cout << "The maps m1 and m3 are equal." << endl;
   else
      cout << "The maps m1 and m3 are not equal." << endl;
}
\* Output:
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
*\
```

## <a name="op_gt"></a>  Operator&gt;

Sprawdza, czy obiekt mapy po lewej stronie operatora jest większy niż obiekt mapy po prawej stronie.

```cpp
bool operator>(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `map`.

*right*<br/>
Obiekt typu `map`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli mapa po lewej stronie operatora jest większy niż mapa po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów mapy opiera się na parowania porównania ich elementów. Większą-niż relacji między dwoma obiektami opiera się na porównanie pierwszy pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// map_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The map m1 is greater than the map m2." << endl;
   else
      cout << "The map m1 is not greater than the map m2." << endl;

   if ( m1 > m3 )
      cout << "The map m1 is greater than the map m3." << endl;
   else
      cout << "The map m1 is not greater than the map m3." << endl;
}
\* Output:
The map m1 is not greater than the map m2.
The map m1 is greater than the map m3.
*\
```

## <a name="op_gt_eq"></a>  Operator&gt;=

Sprawdza, czy obiekt mapy po lewej stronie operatora jest większy lub równy obiektowi mapy po prawej stronie.

```cpp
bool operator>=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `map`.

*right*<br/>
Obiekt typu `map`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli mapa po lewej stronie operatora jest większy niż lub równe do mapy po prawej stronie listy; w przeciwnym **false**.

### <a name="example"></a>Przykład

```cpp
// map_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "Map m1 is greater than or equal to map m2." << endl;
   else
      cout << "The map m1 is less than the map m2." << endl;

   if ( m1 >= m3 )
      cout << "Map m1 is greater than or equal to map m3." << endl;
   else
      cout << "The map m1 is less than the map m3." << endl;

   if ( m1 >= m4 )
      cout << "Map m1 is greater than or equal to map m4." << endl;
   else
      cout << "The map m1 is less than the map m4." << endl;
}
\* Output:
The map m1 is less than the map m2.
Map m1 is greater than or equal to map m3.
Map m1 is greater than or equal to map m4.
*\
```

## <a name="op_neq_multimap"></a>  Operator! = (multimap)

Sprawdza, czy obiekt multimap po lewej stronie operatora nie jest równy obiektowi multimap — po prawej stronie.

```cpp
bool operator!=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `multimap`.

*right*<br/>
Obiekt typu `multimap`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** multimaps nie są równe; **false** Jeśli multimaps są takie same.

### <a name="remarks"></a>Uwagi

Porównanie obiektów multimap opiera się na parowania porównania ich elementów. Dwa multimaps są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

### <a name="example"></a>Przykład

```cpp
// multimap_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The multimaps m1 and m2 are not equal." << endl;
   else
      cout << "The multimaps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The multimaps m1 and m3 are not equal." << endl;
   else
      cout << "The multimaps m1 and m3 are equal." << endl;
}
\* Output:
The multimaps m1 and m2 are not equal.
The multimaps m1 and m3 are equal.
*\
```

## <a name="op_lt_multimap"></a>  Operator&lt;

Sprawdza, czy multimap — obiekt po lewej stronie operatora jest mniejszy niż obiekt multimap — po prawej stronie.

```cpp
bool operator<(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `multimap`.

*right*<br/>
Obiekt typu `multimap`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli mapa wielokrotna po lewej stronie operatora jest mniejsza niż multimap po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów multimap opiera się na parowania porównania ich elementów. Mniej-niż relacji między dwoma obiektami opiera się na porównanie pierwszy pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// multimap_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The multimap m1 is less than the multimap m2." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m2." << endl;

   if ( m1 < m3 )
      cout << "The multimap m1 is less than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m3." << endl;
}
\* Output:
The multimap m1 is less than the multimap m2.
The multimap m1 is not less than the multimap m3.
*\
```

## <a name="eq_multimap"></a>  Operator&lt;=

Sprawdza, czy mapa wielokrotna obiektu po lewej stronie operatora jest mniejszy niż lub równy obiektowi multimap — po prawej stronie.

```cpp
bool operator<=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `multimap`.

*right*<br/>
Obiekt typu `multimap`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli mapa wielokrotna po lewej stronie operatora jest mniejszy niż lub równa multimap po prawej stronie operatora; w przeciwnym **false**.

### <a name="example"></a>Przykład

```cpp
// multimap_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "m1 is less than or equal to m2" << endl;
   else
      cout << "m1 is greater than m2" << endl;

   if ( m1 <= m3 )
      cout << "m1 is less than or equal to m3" << endl;
   else
      cout << "m1 is greater than m3" << endl;

   if ( m1 <= m4 )
      cout << "m1 is less than or equal to m4" << endl;
   else
      cout << "m1 is greater than m4" << endl;
}
\* Output:
m1 is less than or equal to m2
m1 is greater than m3
m1 is less than or equal to m4
*\
```

## <a name="op_eq_eq_multimap"></a>  operator ==

Sprawdza, czy multimap — obiekt po lewej stronie operatora jest równy obiektowi multimap — po prawej stronie.

```cpp
bool operator==(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `multimap`.

*right*<br/>
Obiekt typu `multimap`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli mapa wielokrotna po lewej stronie operatora jest równy multimap po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów multimap opiera się na parowania porównania ich elementów. Dwa multimaps są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

### <a name="example"></a>Przykład

```cpp
// multimap_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      m1.insert(Int_Pair(i, i));
      m2.insert(Int_Pair(i, i*i));
      m3.insert(Int_Pair(i, i));
   }

   if ( m1 == m2 )
      cout << "m1 and m2 are equal" << endl;
   else
      cout << "m1 and m2 are not equal" << endl;

   if ( m1 == m3 )
      cout << "m1 and m3 are equal" << endl;
   else
      cout << "m1 and m3 are not equal" << endl;
}
\* Output:
m1 and m2 are not equal
m1 and m3 are equal
*\
```

## <a name="op_gt_multimap"></a>  Operator&gt;

Sprawdza, czy multimap — obiekt po lewej stronie operatora jest większy niż multimap obiektu po prawej stronie.

```cpp
bool operator>(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `multimap`.

*right*<br/>
Obiekt typu `multimap`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli mapa wielokrotna po lewej stronie operatora jest większy niż mapa wielokrotna po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów multimap opiera się na parowania porównania ich elementów. Większą-niż relacji między dwoma obiektami opiera się na porównanie pierwszy pary nierówne elementów.

### <a name="example"></a>Przykład

```cpp
// multimap_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The multimap m1 is greater than the multimap m2." << endl;
   else
      cout << "Multimap m1 is not greater than multimap m2." << endl;

   if ( m1 > m3 )
      cout << "The multimap m1 is greater than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not greater than the multimap m3." << endl;
}
\* Output:
Multimap m1 is not greater than multimap m2.
The multimap m1 is greater than the multimap m3.
*\
```

## <a name="op_gt_eq_multimap"></a>  Operator&gt;=

Sprawdza, czy multimap — obiekt po lewej stronie operatora jest większy lub równy obiektowi multimap — po prawej stronie.

```cpp
bool operator>=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `multimap`.

*right*<br/>
Obiekt typu `multimap`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli multimap po lewej stronie operatora jest większy niż lub równa multimap po prawej stronie listy; w przeciwnym **false**.

### <a name="example"></a>Przykład

```cpp
// multimap_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "The multimap m1 is greater than or equal to the multimap m2." << endl;
   else
      cout << "The multimap m1 is less than the multimap m2." << endl;

   if ( m1 >= m3 )
      cout << "The multimap m1 is greater than or equal to the multimap m3." << endl;
   else
      cout << "The multimap m1 is less than the multimap m3." << endl;

   if ( m1 >= m4 )
      cout << "The multimap m1 is greater than or equal to the multimap m4." << endl;
   else
      cout << "The multimap m1 is less than the multimap m4." << endl;
}
\* Output:
The multimap m1 is less than the multimap m2.
The multimap m1 is greater than or equal to the multimap m3.
The multimap m1 is greater than or equal to the multimap m4.
*\
```

## <a name="see-also"></a>Zobacz także

[\<Mapa >](../standard-library/map.md)<br/>

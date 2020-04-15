---
title: '&lt;&gt; operatorzy unordered_map'
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: f062c4fd0332525a8b8940d2d93df41df56d2baa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373126"
---
# <a name="ltunordered_mapgt-operators"></a>&lt;&gt; operatorzy unordered_map

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="operator"></a><a name="op_neq"></a>operator!=

Sprawdza, czy [obiekt unordered_map](../standard-library/unordered-map-class.md) po lewej stronie operatora nie jest równy obiektowi unordered_map po prawej stronie.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `unordered_map`.

*Prawo*\
Obiekt typu `unordered_map`.

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli unordered_maps nie są równe; **false,** jeśli są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_map nie ma wpływu na dowolną kolejność, w której przechowują swoje elementy. Dwa unordered_maps są równe, jeśli mają taką samą liczbę elementów i elementy w jednym kontenerze są permutacji elementów w innym kontenerze. W przeciwnym razie są nierówne.

### <a name="example"></a>Przykład

```cpp
// unordered_map_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}
```

**Wyjście:**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="operator"></a><a name="op_eq_eq"></a>operator==

Sprawdza, czy [obiekt unordered_map](../standard-library/unordered-map-class.md) po lewej stronie operatora jest równy unordered_map obiektowi po prawej stronie.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `unordered_map`.

*Prawo*\
Obiekt typu `unordered_map`.

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli unordered_maps są równe; **false,** jeśli nie są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_map nie ma wpływu na dowolną kolejność, w której przechowują swoje elementy. Dwa unordered_maps są równe, jeśli mają taką samą liczbę elementów i elementy w jednym kontenerze są permutacji elementów w innym kontenerze. W przeciwnym razie są nierówne.

### <a name="example"></a>Przykład

```cpp
// unordered_map_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}
```

**Wyjście:**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="operator"></a><a name="op_neq_multimap"></a>operator!=

Sprawdza, czy [obiekt unordered_multimap](../standard-library/unordered-multimap-class.md) po lewej stronie operatora nie jest równy obiektowi unordered_multimap po prawej stronie.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `unordered_multimap`.

*Prawo*\
Obiekt typu `unordered_multimap`.

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli unordered_multimaps nie są równe; **false,** jeśli są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_multimap nie ma wpływu na dowolną kolejność, w której przechowują swoje elementy. Dwa unordered_multimaps są równe, jeśli mają taką samą liczbę elementów i elementy w jednym kontenerze są permutacji elementów w innym kontenerze. W przeciwnym razie nie są równe.

### <a name="example"></a>Przykład

```cpp
// unordered_multimap_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}
```

**Wyjście:**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="operator"></a><a name="op_eq_eq_multimap"></a>operator==

Sprawdza, czy [obiekt unordered_multimap](../standard-library/unordered-multimap-class.md) po lewej stronie operatora jest równy unordered_multimap obiektowi po prawej stronie.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `unordered_multimap`.

*Prawo*\
Obiekt typu `unordered_multimap`.

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli unordered_multimaps są równe; **false,** jeśli nie są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_multimap nie ma wpływu na dowolną kolejność, w której przechowują swoje elementy. Dwa unordered_multimaps są równe, jeśli mają taką samą liczbę elementów i elementy w jednym kontenerze są permutacji elementów w innym kontenerze. W przeciwnym razie są nierówne.

### <a name="example"></a>Przykład

```cpp
// unordered_multimap_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}
```

**Wyjście:**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="see-also"></a>Zobacz też

[<unordered_map>](../standard-library/unordered-map.md)

---
title: '&lt;unordered_map operatory&gt;'
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: fe4877bc5b371a2570c18950bac36a003078ccc7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422550"
---
# <a name="ltunordered_mapgt-operators"></a>&lt;unordered_map operatory&gt;

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator = =](#op_eq_eq)|[operator!=](#op_neq_multimap)|[operator = =](#op_eq_eq_multimap)|

## <a name="op_neq"></a>operator! =

Testuje, czy obiekt [unordered_map](../standard-library/unordered-map-class.md) po lewej stronie operatora nie jest równy obiektowi unordered_map po prawej stronie.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `unordered_map`.

*prawa*\
Obiekt typu `unordered_map`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , Jeśli unordered_maps nie są równe; **Fałsz** , jeśli są równe.

### <a name="remarks"></a>Uwagi

Do porównania między obiektami unordered_map nie ma wpływ dowolne zamówienie, w którym są przechowywane elementy. Dwie unordered_maps są równe, jeśli mają taką samą liczbę elementów, a elementy w jednym kontenerze są Permutacją elementów w innym kontenerze. W przeciwnym razie są one nierówne.

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

**Rozdzielczości**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt [unordered_map](../standard-library/unordered-map-class.md) po lewej stronie operatora jest równy obiektowi unordered_map po prawej stronie.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `unordered_map`.

*prawa*\
Obiekt typu `unordered_map`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , Jeśli unordered_maps są równe; **wartość false** , jeśli nie są równe.

### <a name="remarks"></a>Uwagi

Do porównania między obiektami unordered_map nie ma wpływ dowolne zamówienie, w którym są przechowywane elementy. Dwie unordered_maps są równe, jeśli mają taką samą liczbę elementów, a elementy w jednym kontenerze są Permutacją elementów w innym kontenerze. W przeciwnym razie są one nierówne.

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

**Rozdzielczości**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="op_neq_multimap"></a>operator! =

Testuje, czy obiekt [unordered_multimap](../standard-library/unordered-multimap-class.md) po lewej stronie operatora nie jest równy obiektowi unordered_multimap po prawej stronie.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `unordered_multimap`.

*prawa*\
Obiekt typu `unordered_multimap`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli unordered_multimaps nie są równe; **Fałsz** , jeśli są równe.

### <a name="remarks"></a>Uwagi

Do porównania między obiektami unordered_multimap nie ma wpływ dowolne zamówienie, w którym są przechowywane elementy. Dwie unordered_multimaps są równe, jeśli mają taką samą liczbę elementów, a elementy w jednym kontenerze są Permutacją elementów w innym kontenerze. W przeciwnym razie nie są równe.

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

**Rozdzielczości**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq_multimap"></a>operator = =

Testuje, czy obiekt [unordered_multimap](../standard-library/unordered-multimap-class.md) po lewej stronie operatora jest równy obiektowi unordered_multimap po prawej stronie.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `unordered_multimap`.

*prawa*\
Obiekt typu `unordered_multimap`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli unordered_multimaps są równe; **wartość false** , jeśli nie są równe.

### <a name="remarks"></a>Uwagi

Do porównania między obiektami unordered_multimap nie ma wpływ dowolne zamówienie, w którym są przechowywane elementy. Dwie unordered_multimaps są równe, jeśli mają taką samą liczbę elementów, a elementy w jednym kontenerze są Permutacją elementów w innym kontenerze. W przeciwnym razie są one nierówne.

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

**Rozdzielczości**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="see-also"></a>Zobacz też

[<unordered_map>](../standard-library/unordered-map.md)

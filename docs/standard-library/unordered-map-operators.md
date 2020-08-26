---
title: '&lt;&gt;operatory unordered_map'
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: 0ecedcfa8444b5cbae8fbe64b528a593ed3498b4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844252"
---
# <a name="ltunordered_mapgt-operators"></a>&lt;&gt;operatory unordered_map

[unordered_map:: operator! =](#op_neq)\
[unordered_map:: operator = =](#op_eq_eq)\
[unordered_multimap:: operator! =](#op_neq_multimap)\
[unordered_multimap:: operator = =](#op_eq_eq_multimap)

## <a name="operator"></a><a name="op_neq"></a> operator! =

Testuje, czy obiekt [unordered_map](../standard-library/unordered-map-class.md) po lewej stronie operatora nie jest równy obiektowi unordered_map po prawej stronie.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `unordered_map`.

*Kliknij*\
Obiekt typu `unordered_map`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli unordered_maps nie są równe; **`false`** Jeśli są równe.

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

/* Output:
um1 != um2: true
um1 != um3: false
um2 != um3: true
*/
```

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

Testuje, czy obiekt [unordered_map](../standard-library/unordered-map-class.md) po lewej stronie operatora jest równy obiektowi unordered_map po prawej stronie.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `unordered_map`.

*Kliknij*\
Obiekt typu `unordered_map`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli unordered_maps są równe; **`false`** Jeśli nie są równe.

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

/* Output:
um1 == um2: false
um1 == um3: true
um2 == um3: false
*/
```

## <a name="operator"></a><a name="op_neq_multimap"></a> operator! =

Testuje, czy obiekt [unordered_multimap](../standard-library/unordered-multimap-class.md) po lewej stronie operatora nie jest równy obiektowi unordered_multimap po prawej stronie.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `unordered_multimap`.

*Kliknij*\
Obiekt typu `unordered_multimap`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli unordered_multimaps nie są równe; **`false`** Jeśli są równe.

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

/* Output:
um1 != um2: true
um1 != um3: false
um2 != um3: true
*/
```

## <a name="operator"></a><a name="op_eq_eq_multimap"></a> operator = =

Testuje, czy obiekt [unordered_multimap](../standard-library/unordered-multimap-class.md) po lewej stronie operatora jest równy obiektowi unordered_multimap po prawej stronie.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `unordered_multimap`.

*Kliknij*\
Obiekt typu `unordered_multimap`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli unordered_multimaps są równe; **`false`** Jeśli nie są równe.

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

/* Output:
um1 == um2: false
um1 == um3: true
um2 == um3: false
*/
```

## <a name="see-also"></a>Zobacz też

[<unordered_map>](../standard-library/unordered-map.md)

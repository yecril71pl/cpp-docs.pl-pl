---
title: '&lt;unordered_map —&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
dev_langs:
- C++
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: 69a53ae6b54248f5b9938e2c9137a24f441c061d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859355"
---
# <a name="ltunorderedmapgt-operators"></a>&lt;unordered_map —&gt; operatory

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="op_neq"></a>  operator! =

Testy czy [unordered_map](../standard-library/unordered-map-class.md) obiekt po lewej stronie operatora nie jest taki sam jak obiekt unordered_map po prawej stronie.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `unordered_map`.

`right` Obiekt typu `unordered_map`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli unordered_maps nie są równe; `false` czy są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_map nie ma wpływu na dowolne kolejność, w którym są przechowywane ich elementów. Dwa unordered_maps są takie same, jeśli mają taką samą liczbę elementów i elementów w jeden kontener są permutacji elementów w kontenerze innym. W przeciwnym razie ich nie są równe.

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

**Dane wyjściowe:**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq"></a>  operator ==

Testy czy [unordered_map](../standard-library/unordered-map-class.md) obiekt po lewej stronie operatora jest taki sam jak obiekt unordered_map po prawej stronie.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `unordered_map`.

`right` Obiekt typu `unordered_map`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli unordered_maps są równe; `false` nie są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_map nie ma wpływu na dowolne kolejność, w którym są przechowywane ich elementów. Dwa unordered_maps są takie same, jeśli mają taką samą liczbę elementów i elementów w jeden kontener są permutacji elementów w kontenerze innym. W przeciwnym razie ich nie są równe.

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

**Dane wyjściowe:**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="op_neq_multimap"></a>  operator! =

Testy czy [unordered_multimap](../standard-library/unordered-multimap-class.md) obiekt po lewej stronie operatora nie jest taki sam jak obiekt unordered_multimap po prawej stronie.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `unordered_multimap`.

`right` Obiekt typu `unordered_multimap`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli unordered_multimaps nie są równe; `false` czy są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_multimap nie ma wpływu na dowolne kolejność, w którym są przechowywane ich elementów. Dwa unordered_multimaps są takie same, jeśli mają taką samą liczbę elementów i elementów w jeden kontener są permutacji elementów w kontenerze innym. W przeciwnym razie nie są one takie same.

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

**Dane wyjściowe:**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq_multimap"></a>  operator ==

Testy czy [unordered_multimap](../standard-library/unordered-multimap-class.md) obiekt po lewej stronie operatora jest taki sam jak obiekt unordered_multimap po prawej stronie.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `unordered_multimap`.

`right` Obiekt typu `unordered_multimap`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli unordered_multimaps są równe; `false` nie są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_multimap nie ma wpływu na dowolne kolejność, w którym są przechowywane ich elementów. Dwa unordered_multimaps są takie same, jeśli mają taką samą liczbę elementów i elementów w jeden kontener są permutacji elementów w kontenerze innym. W przeciwnym razie ich nie są równe.

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

**Dane wyjściowe:**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="see-also"></a>Zobacz także

[<unordered_map>](../standard-library/unordered-map.md)<br/>

---
title: '&lt;&gt; operatorzy hash_map'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: ed143349f3afc7a27ad565c1cc929c6ecb5f6ad8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375445"
---
# <a name="lthash_mapgt-operators"></a>&lt;&gt; operatorzy hash_map

|||
|-|-|
|[operator!=](#op_neq)|[operator!= (multimap)](#op_neq_mm)|
|[operator==](#op_eq_eq)|[operator== (multimap)](#op_eq_eq_mm)|

## <a name="operator"></a><a name="op_neq"></a>operator!=

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map Klasa](unordered-map-class.md).

Sprawdza, czy obiekt hash_map po lewej stronie operatora nie jest równy hash_map obiektowi po prawej stronie.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `hash_map`.

*Prawo*\
Obiekt typu `hash_map`.

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli hash_maps nie są równe; **false,** jeśli hash_maps są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów hash_map opiera się na parowym porównaniu ich elementów. Dwa hash_maps są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

Członkowie [<hash_map>](hash-map.md) i<hash_set [>](hash-set.md) plików nagłówkowych w obszarze [nazw stdext](stdext-namespace.md).

### <a name="example"></a>Przykład

```cpp
// hash_map_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a>operator==

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map Klasa](unordered-map-class.md).

Sprawdza, czy obiekt hash_map po lewej stronie operatora jest równy hash_map obiektowi po prawej stronie.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `hash_map`.

*Prawo*\
Obiekt typu `hash_map`.

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeżeli hash_map po lewej stronie operatora jest równa hash_map po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów hash_map opiera się na parowym porównaniu ich elementów. Dwa hash_maps są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

### <a name="example"></a>Przykład

```cpp
// hash_map_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 == hm2 )
      cout << "The hash_maps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator-hash_multimap"></a><a name="op_neq_mm"></a>operator!= (hash_multimap)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](unordered-multimap-class.md).

Sprawdza, czy obiekt hash_multimap po lewej stronie operatora nie jest równy obiektowi hash_multimap po prawej stronie.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `hash_multimap`.

*Prawo*\
Obiekt typu `hash_multimap`.

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli hash_multimaps nie są równe; **false,** jeśli hash_multimaps są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów hash_multimap opiera się na parowym porównaniu ich elementów. Dwa hash_multimaps są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="operator--hash_multimap"></a><a name="op_eq_eq_mm"></a>operator== (hash_multimap)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](unordered-multimap-class.md).

Sprawdza, czy obiekt hash_multimap po lewej stronie operatora jest równy hash_multimap obiektowi po prawej stronie.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `hash_multimap`.

*Prawo*\
Obiekt typu `hash_multimap`.

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeżeli hash_multimap po lewej stronie operatora jest równa hash_multimap po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów hash_multimap opiera się na parowym porównaniu ich elementów. Dwa hash_multimaps są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

### <a name="example"></a>Przykład

```cpp
// hash_multimap_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1, hm2, hm3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      hm1.insert(Int_Pair(i, i));
      hm2.insert(Int_Pair(i, i*i));
      hm3.insert(Int_Pair(i, i));
   }

   if ( hm1 == hm2 )
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="see-also"></a>Zobacz też

[<hash_map>](hash-map.md)

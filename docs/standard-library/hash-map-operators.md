---
title: '&lt;hash_map —&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
dev_langs:
- C++
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: aa5c2a662fb5e827978a7c00aa3035dcc6cc97f2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="lthashmapgt-operators"></a>&lt;hash_map —&gt; operatory

|||
|-|-|
|[operator!=](#op_neq)|[Operator! = (multimap)](#op_neq_mm)|
|[operator==](#op_eq_eq)|[operator== (multimap)](#op_eq_eq_mm)|

## <a name="op_neq"></a>  operator! =

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](unordered-map-class.md).

Testy, jeśli obiekt hash_map po lewej stronie operatora nie jest taki sam jak obiekt hash_map po prawej stronie.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `hash_map`.

`right` Obiekt typu `hash_map`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** hash_maps nie są równe; **false** hash_maps są równe.

### <a name="remarks"></a>Uwagi

Porównanie hash_map — obiekty opiera się na parowania porównanie ich elementów. Dwa hash_maps są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

Elementy członkowskie [< hash_map >](hash-map.md) i [< hash_set >](hash-set.md) pliki nagłówkowe w [ stdext — Namespace](stdext-namespace.md).

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

## <a name="op_eq_eq"></a>  operator ==

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](unordered-map-class.md).

Testy, jeśli obiekt hash_map po lewej stronie operatora jest taki sam jak obiekt hash_map po prawej stronie.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `hash_map`.

`right` Obiekt typu `hash_map`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli hash_map po lewej stronie operatora jest równa hash_map po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie hash_map — obiekty opiera się na parowania porównanie ich elementów. Dwa hash_maps są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

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

## <a name="op_neq_mm"></a>  Operator! = (hash_multimap)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](unordered-multimap-class.md).

Testy, jeśli obiekt hash_multimap po lewej stronie operatora nie jest taki sam jak obiekt hash_multimap po prawej stronie.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `hash_multimap`.

`right` Obiekt typu `hash_multimap`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** hash_multimaps nie są równe; **false** hash_multimaps są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów hash_multimap jest oparta na parowania porównanie ich elementów. Dwa hash_multimaps są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

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

## <a name="op_eq_eq_mm"></a>  Operator == (hash_multimap)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](unordered-multimap-class.md).

Testy, jeśli obiekt hash_multimap po lewej stronie operatora jest taki sam jak obiekt hash_multimap po prawej stronie.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `hash_multimap`.

`right` Obiekt typu `hash_multimap`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli hash_multimap po lewej stronie operatora jest równa hash_multimap po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów hash_multimap jest oparta na parowania porównanie ich elementów. Dwa hash_multimaps są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

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

## <a name="see-also"></a>Zobacz także

[<hash_map>](hash-map.md)<br/>

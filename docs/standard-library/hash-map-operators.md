---
title: '&lt;hash_map —&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: ba84f476c712f64e7782f0ea476bbb65a35dc14a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559708"
---
# <a name="lthashmapgt-operators"></a>&lt;hash_map —&gt; operatorów

|||
|-|-|
|[operator!=](#op_neq)|[Operator! = (multimap)](#op_neq_mm)|
|[operator==](#op_eq_eq)|[operator== (multimap)](#op_eq_eq_mm)|

## <a name="op_neq"></a>  operator! =

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map, klasa](unordered-map-class.md).

Sprawdza, czy obiekt hash_map po lewej stronie operatora nie jest równy obiektowi hash_map po prawej stronie.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `hash_map`.

*right*<br/>
Obiekt typu `hash_map`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** hash_maps nie są równe; **false** hash_maps są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów hash_map opiera się na parowania porównania ich elementów. Dwa hash_maps są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

Elementy członkowskie [< hash_map >](hash-map.md) i [< hash_set >](hash-set.md) pliki nagłówkowe w [ stdext Namespace](stdext-namespace.md).

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
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map, klasa](unordered-map-class.md).

Sprawdza, czy obiekt hash_map po lewej stronie operatora jest równy obiektowi hash_map po prawej stronie.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `hash_map`.

*right*<br/>
Obiekt typu `hash_map`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli hash_map po lewej stronie operatora jest równy hash_map po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów hash_map opiera się na parowania porównania ich elementów. Dwa hash_maps są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](unordered-multimap-class.md).

Sprawdza, czy obiekt hash_multimap po lewej stronie operatora nie jest równy obiektowi hash_multimap po prawej stronie.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `hash_multimap`.

*right*<br/>
Obiekt typu `hash_multimap`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** hash_multimaps nie są równe; **false** hash_multimaps są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów hash_multimap opiera się na parowania porównania ich elementów. Dwa hash_multimaps są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](unordered-multimap-class.md).

Sprawdza, czy obiekt hash_multimap po lewej stronie operatora jest równy obiektowi hash_multimap po prawej stronie.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `hash_multimap`.

*right*<br/>
Obiekt typu `hash_multimap`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli hash_multimap po lewej stronie operatora jest równy hash_multimap po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów hash_multimap opiera się na parowania porównania ich elementów. Dwa hash_multimaps są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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

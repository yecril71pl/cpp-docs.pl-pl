---
title: '&lt;hash_map operatory&gt;'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: c4cc73feb3c8163a2be9f0122f57eaa0fb8ab3b8
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419015"
---
# <a name="lthash_mapgt-operators"></a>&lt;hash_map operatory&gt;

|||
|-|-|
|[operator!=](#op_neq)|[operator! = (multimap)](#op_neq_mm)|
|[operator = =](#op_eq_eq)|[operator = = (multimap)](#op_eq_eq_mm)|

## <a name="op_neq"></a>operator! =

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_map](unordered-map-class.md).

Testuje, czy obiekt hash_map po lewej stronie operatora nie jest równy obiektowi hash_map po prawej stronie.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `hash_map`.

*prawa*\
Obiekt typu `hash_map`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli hash_maps nie są równe; **wartość false** , jeśli hash_maps są równe.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami hash_map jest oparte na porównaniu z przełączaniem ich elementów. Dwie hash_maps są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

Elementy członkowskie [< hash_map >](hash-map.md) i [< hash_set](hash-set.md) > plików nagłówkowych w [przestrzeni nazw stdext](stdext-namespace.md).

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

## <a name="op_eq_eq"></a>operator = =

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_map](unordered-map-class.md).

Testuje, czy obiekt hash_map po lewej stronie operatora jest równy obiektowi hash_map po prawej stronie.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `hash_map`.

*prawa*\
Obiekt typu `hash_map`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli hash_map po lewej stronie operatora jest równy hash_map po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami hash_map jest oparte na porównaniu z przełączaniem ich elementów. Dwie hash_maps są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

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

## <a name="op_neq_mm"></a>operator! = (hash_multimap)

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multimap](unordered-multimap-class.md).

Testuje, czy obiekt hash_multimap po lewej stronie operatora nie jest równy obiektowi hash_multimap po prawej stronie.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `hash_multimap`.

*prawa*\
Obiekt typu `hash_multimap`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli hash_multimaps nie są równe; **wartość false** , jeśli hash_multimaps są równe.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami hash_multimap jest oparte na porównaniu z przełączaniem ich elementów. Dwie hash_multimaps są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

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

## <a name="op_eq_eq_mm"></a>operator = = (hash_multimap)

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_multimap](unordered-multimap-class.md).

Testuje, czy obiekt hash_multimap po lewej stronie operatora jest równy obiektowi hash_multimap po prawej stronie.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `hash_multimap`.

*prawa*\
Obiekt typu `hash_multimap`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli hash_multimap po lewej stronie operatora jest równy hash_multimap po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami hash_multimap jest oparte na porównaniu z przełączaniem ich elementów. Dwie hash_multimaps są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

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

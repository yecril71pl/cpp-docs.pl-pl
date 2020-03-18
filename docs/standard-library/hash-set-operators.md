---
title: '&lt;hash_set operatory&gt;'
ms.date: 03/27/2019
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
ms.openlocfilehash: 3900e9c6e4fb7f5a163279165a51b440d138a8e5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419001"
---
# <a name="lthash_setgt-operators"></a>&lt;hash_set operatory&gt;

||||
|-|-|-|
|[operator!=](#op_neq)|[operator! = (hash_multiset)](#op_neq_hash_multiset)|[operator = =](#op_eq_eq)|
|[operator = = (hash_multiset)](#op_eq_eq_hash_multiset)|

## <a name="op_neq"></a>operator! =

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Testuje, czy obiekt hash_set po lewej stronie operatora nie jest równy obiektowi hash_set po prawej stronie.

```cpp
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `hash_set`.

*prawa*\
Obiekt typu `hash_set`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli hash_sets nie są równe; **wartość false** , jeśli hash_sets są równe.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami hash_set jest oparte na porównaniu z przełączaniem między swoimi elementami. Dwie hash_sets są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

Elementy członkowskie [< hash_map >](../standard-library/hash-map.md) i [< hash_set](../standard-library/hash-set.md) > pliki nagłówkowe znajdują się w [przestrzeni nazw stdext](../standard-library/stdext-namespace.md).

### <a name="example"></a>Przykład

```cpp
// hash_set_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_sets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_sets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_sets hs1 and hs2 are not equal.
The hash_sets hs1 and hs3 are equal.
```

## <a name="op_eq_eq"></a>operator = =

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Testuje, czy obiekt hash_set po lewej stronie operatora jest równy obiektowi hash_set po prawej stronie.

```cpp
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `hash_set`.

*prawa*\
Obiekt typu `hash_set`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli hash_set po lewej stronie operatora jest równy hash_set po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami hash_set jest oparte na porównaniu z przełączaniem ich elementów. Dwie hash_sets są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

### <a name="example"></a>Przykład

```cpp
// hash_set_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_sets s1 and s2 are equal." << endl;
   else
      cout << "The hash_sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_sets s1 and s3 are equal." << endl;
   else
      cout << "The hash_sets s1 and s3 are not equal." << endl;
}
```

```Output
The hash_sets s1 and s2 are not equal.
The hash_sets s1 and s3 are equal.
```

## <a name="op_neq_hash_multiset"></a>operator! = (hash_multiset)

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Testuje, czy obiekt hash_multiset po lewej stronie operatora nie jest równy obiektowi hash_multiset po prawej stronie.

```cpp
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `hash_multiset`.

*prawa*\
Obiekt typu `hash_multiset`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli hash_multisets nie są równe; **wartość false** , jeśli hash_multisets są równe.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami hash_multiset jest oparte na porównaniu z przełączaniem między swoimi elementami. Dwie hash_multisets są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

### <a name="example"></a>Przykład

```cpp
// hashset_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_multisets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_multisets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_multisets hs1 and hs2 are not equal.
The hash_multisets hs1 and hs3 are equal.
```

## <a name="op_eq_eq_hash_multiset"></a>operator = = (hash_multiset)

> [!NOTE]
> {1&gt;Ten interfejs API jest przestarzały.&lt;1} Alternatywą jest [klasa unordered_set](../standard-library/unordered-set-class.md).

Testuje, czy obiekt hash_multiset po lewej stronie operatora jest równy obiektowi hash_multiset po prawej stronie.

```cpp
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `hash_multiset`.

*prawa*\
Obiekt typu `hash_multiset`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli hash_multiset po lewej stronie operatora jest równy hash_multiset po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie między obiektami hash_multiset jest oparte na porównaniu z przełączaniem ich elementów. Dwie hash_multisets są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

### <a name="example"></a>Przykład

```cpp
// hash_multiset_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;
}
```

```Output
The hash_multisets s1 and s2 are not equal.
The hash_multisets s1 and s2 are equal.
```

## <a name="see-also"></a>Zobacz też

[<hash_set>](../standard-library/hash-set.md)

---
title: '&lt;hash_set —&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
dev_langs:
- C++
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
caps.latest.revision: 13
manager: ghogen
ms.openlocfilehash: 9db5096e93a5778682eb9e926ac2b44c334b6349
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="lthashsetgt-operators"></a>&lt;hash_set —&gt; operatory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator! = (hash_multiset)](#op_neq_hash_multiset)|[operator==](#op_eq_eq)|
|[Operator == (hash_multiset)](#op_eq_eq_hash_multiset)|

## <a name="op_neq"></a>  operator! =

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).

Testy, jeśli obiekt hash_set po lewej stronie operatora nie jest taki sam jak obiekt hash_set po prawej stronie.

```cpp
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `hash_set`.

`right` Obiekt typu `hash_set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** hash_sets nie są równe; **false** hash_sets są równe.

### <a name="remarks"></a>Uwagi

Porównanie hash_set — obiekty opiera się na parowania porównanie ich elementów. Dwa hash_sets są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

Elementy członkowskie [< hash_map >](../standard-library/hash-map.md) i [< hash_set >](../standard-library/hash-set.md) pliki nagłówka są [stdext — Namespace](../standard-library/stdext-namespace.md).

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

## <a name="op_eq_eq"></a>  operator ==

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).

Testy, jeśli obiekt hash_set po lewej stronie operatora jest taki sam jak obiekt hash_set po prawej stronie.

```cpp
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `hash_set`.

`right` Obiekt typu `hash_set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli hash_set po lewej stronie operatora jest równa hash_set po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie hash_set — obiekty opiera się na parowania porównanie ich elementów. Dwa hash_sets są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

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

## <a name="neq_hash_multiset"></a>  Operator! = (hash_multiset)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).

Testy, jeśli obiekt hash_multiset po lewej stronie operatora nie jest taki sam jak obiekt hash_multiset po prawej stronie.

```cpp
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `hash_multiset`.

`right` Obiekt typu `hash_multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** hash_multisets nie są równe; **false** hash_multisets są równe.

### <a name="remarks"></a>Uwagi

Porównanie hash_multiset — obiekty opiera się na parowania porównanie ich elementów. Dwa hash_multisets są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

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

## <a name="eq_eq_hash_multiset"></a>  Operator == (hash_multiset)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).

Testy, jeśli obiekt hash_multiset po lewej stronie operatora jest taki sam jak obiekt hash_multiset po prawej stronie.

```cpp
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `hash_multiset`.

`right` Obiekt typu `hash_multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli hash_multiset po lewej stronie operatora jest równa hash_multiset po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie hash_multiset — obiekty opiera się na parowania porównanie ich elementów. Dwa hash_multisets są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.

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

## <a name="see-also"></a>Zobacz także

[<hash_set>](../standard-library/hash-set.md)<br/>

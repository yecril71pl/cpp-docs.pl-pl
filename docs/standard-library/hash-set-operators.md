---
title: '&lt;hash_set —&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
ms.openlocfilehash: 3cb0b743eefa52b178a89be1c2cc766352bf4849
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564843"
---
# <a name="lthashsetgt-operators"></a>&lt;hash_set —&gt; operatorów

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator! = (hash_multiset)](#op_neq_hash_multiset)|[operator==](#op_eq_eq)|
|[Operator == (hash_multiset)](#op_eq_eq_hash_multiset)|

## <a name="op_neq"></a>  operator! =

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Sprawdza, czy obiekt hash_set po lewej stronie operatora nie jest równy obiektowi hash_set po prawej stronie.

```cpp
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `hash_set`.

*right*<br/>
Obiekt typu `hash_set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** hash_sets nie są równe; **false** hash_sets są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów hash_set opiera się na parowania porównanie ich elementów. Dwa hash_sets są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

Elementy członkowskie [< hash_map >](../standard-library/hash-map.md) i [< hash_set >](../standard-library/hash-set.md) pliki nagłówkowe są [stdext Namespace](../standard-library/stdext-namespace.md).

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
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Sprawdza, czy obiekt hash_set po lewej stronie operatora jest równy obiektowi hash_set po prawej stronie.

```cpp
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `hash_set`.

*right*<br/>
Obiekt typu `hash_set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli hash_set po lewej stronie operatora jest równy hash_set po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów hash_set opiera się na parowania porównania ich elementów. Dwa hash_sets są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Sprawdza, czy obiekt hash_multiset po lewej stronie operatora nie jest równy obiektowi hash_multiset po prawej stronie.

```cpp
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `hash_multiset`.

*right*<br/>
Obiekt typu `hash_multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** hash_multisets nie są równe; **false** hash_multisets są równe.

### <a name="remarks"></a>Uwagi

Porównanie hash_multiset — obiekty opiera się na parowania porównanie ich elementów. Dwa hash_multisets są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Sprawdza, czy obiekt hash_multiset po lewej stronie operatora jest równy obiektowi hash_multiset po prawej stronie.

```cpp
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `hash_multiset`.

*right*<br/>
Obiekt typu `hash_multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli hash_multiset po lewej stronie operatora jest równy hash_multiset po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Porównanie hash_multiset — obiekty opiera się na parowania porównania ich elementów. Dwa hash_multisets są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

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

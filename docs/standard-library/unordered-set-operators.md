---
title: '&lt;unordered_set —&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- unordered_set/std::operator!=
- unordered_set/std::operator==
dev_langs:
- C++
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
ms.openlocfilehash: c72058f78a779c6fbac91cac07e9ffef1244a046
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860102"
---
# <a name="ltunorderedsetgt-operators"></a>&lt;unordered_set —&gt; operatory

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_unordered_multiset)|[operator==](#op_eq_eq_unordered_multiset)|

## <a name="op_neq"></a>  operator! =

Testy czy [unordered_set](../standard-library/unordered-set-class.md) obiekt po lewej stronie operatora nie jest taki sam jak obiekt unordered_set po prawej stronie.

```cpp
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `unordered_set`.

`right` Obiekt typu `unordered_set`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli unordered_sets nie są równe; `false` czy są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_set nie ma wpływu na dowolne kolejność, w którym są przechowywane ich elementów. Dwa unordered_sets są takie same, jeśli mają taką samą liczbę elementów i elementów w jeden kontener są permutacji elementów w kontenerze innym. W przeciwnym razie ich nie są równe.

### <a name="example"></a>Przykład

```cpp
// unordered_set_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}

```

**Dane wyjściowe:**

`c1 != c2: true`

`c1 != c3: false`

`c2 != c3: true`

## <a name="op_eq_eq"></a>  operator ==

Testy czy [unordered_set](../standard-library/unordered-set-class.md) obiekt po lewej stronie operatora jest taki sam jak obiekt unordered_set po prawej stronie.

```cpp
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `unordered_set`.

`right` Obiekt typu `unordered_set`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli unordered_sets są równe; `false` nie są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_set nie ma wpływu na dowolne kolejność, w którym są przechowywane ich elementów. Dwa unordered_sets są takie same, jeśli mają taką samą liczbę elementów i elementów w jeden kontener są permutacji elementów w kontenerze innym. W przeciwnym razie ich nie są równe.

### <a name="example"></a>Przykład

```cpp
// unordered_set_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}

```

**Dane wyjściowe:**

`c1 == c2: false`

`c1 == c3: true`

`c2 == c3: false`

## <a name="op_neq_unordered_multiset"></a>  operator! =

Testy czy [unordered_multiset](../standard-library/unordered-multiset-class.md) obiekt po lewej stronie operatora nie jest taki sam jak obiekt unordered_multiset po prawej stronie.

```cpp
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `unordered_multiset`.

`right` Obiekt typu `unordered_multiset`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli unordered_multisets nie są równe; `false` czy są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_multiset nie ma wpływu na dowolne kolejność, w którym są przechowywane ich elementów. Dwa unordered_multisets są takie same, jeśli mają taką samą liczbę elementów i elementów w jeden kontener są permutacji elementów w kontenerze innym. W przeciwnym razie ich nie są równe.

### <a name="example"></a>Przykład

```cpp
// unordered_multiset_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}

```

**Dane wyjściowe:**

`c1 != c2: true`

`c1 != c3: false`

`c2 != c3: true`

## <a name="op_eq_eq_unordered_multiset"></a>  operator ==

Testy czy [unordered_multiset](../standard-library/unordered-multiset-class.md) obiekt po lewej stronie operatora jest taki sam jak obiekt unordered_multiset po prawej stronie.

```cpp
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Obiekt typu `unordered_multiset`.

`right` Obiekt typu `unordered_multiset`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli unordered_multisets są równe; `false` nie są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_multiset nie ma wpływu na dowolne kolejność, w którym są przechowywane ich elementów. Dwa unordered_multisets są takie same, jeśli mają taką samą liczbę elementów i elementów w jeden kontener są permutacji elementów w kontenerze innym. W przeciwnym razie ich nie są równe.

### <a name="example"></a>Przykład

```cpp
// unordered_multiset_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}

```

**Dane wyjściowe:**

`c1 == c2: false`

`c1 == c3: true`

`c2 == c3: false`

## <a name="see-also"></a>Zobacz także

[<unordered_set>](../standard-library/unordered-set.md)<br/>

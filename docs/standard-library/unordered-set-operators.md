---
title: '&lt;unordered_set —&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::operator!=
- unordered_set/std::operator==
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
ms.openlocfilehash: 501a65c8725631463e9c2a6b7b11e0c6300b6664
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495020"
---
# <a name="ltunorderedsetgt-operators"></a>&lt;unordered_set —&gt; operatorów

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_unordered_multiset)|[operator==](#op_eq_eq_unordered_multiset)|

## <a name="op_neq"></a>  operator! =

Testy czy [unordered_set](../standard-library/unordered-set-class.md) obiekt po lewej stronie operatora nie jest równy obiektowi unordered_set po prawej stronie.

```cpp
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `unordered_set`.

*right*<br/>
Obiekt typu `unordered_set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** unordered_sets nie są równe; **false** czy są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_set nie dotyczy dowolnego kolejność, w którym są przechowywane ich elementów. Dwa unordered_sets są takie same, jeśli mają taką samą liczbę elementów, a elementy w jeden kontener są permutacji elementy znajdujące się w innych kontenera. W przeciwnym razie są nierówne.

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

Testy czy [unordered_set](../standard-library/unordered-set-class.md) obiektu po lewej stronie operatora jest równy obiektowi unordered_set po prawej stronie.

```cpp
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `unordered_set`.

*right*<br/>
Obiekt typu `unordered_set`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** unordered_sets są równe; **false** nie są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_set nie dotyczy dowolnego kolejność, w którym są przechowywane ich elementów. Dwa unordered_sets są takie same, jeśli mają taką samą liczbę elementów, a elementy w jeden kontener są permutacji elementy znajdujące się w innych kontenera. W przeciwnym razie są nierówne.

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

Testy czy [unordered_multiset](../standard-library/unordered-multiset-class.md) obiekt po lewej stronie operatora nie jest równy obiektowi unordered_multiset po prawej stronie.

```cpp
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `unordered_multiset`.

*right*<br/>
Obiekt typu `unordered_multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** unordered_multisets nie są równe; **false** czy są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_multiset nie dotyczy dowolnego kolejność, w którym są przechowywane ich elementy. Dwa unordered_multisets są takie same, jeśli mają taką samą liczbę elementów, a elementy w jeden kontener są permutacji elementy znajdujące się w innych kontenera. W przeciwnym razie są nierówne.

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

Testy czy [unordered_multiset](../standard-library/unordered-multiset-class.md) obiektu po lewej stronie operatora jest równy obiektowi unordered_multiset po prawej stronie.

```cpp
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Obiekt typu `unordered_multiset`.

*right*<br/>
Obiekt typu `unordered_multiset`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** unordered_multisets są równe; **false** nie są równe.

### <a name="remarks"></a>Uwagi

Porównanie obiektów unordered_multiset nie dotyczy dowolnego kolejność, w którym są przechowywane ich elementy. Dwa unordered_multisets są takie same, jeśli mają taką samą liczbę elementów, a elementy w jeden kontener są permutacji elementy znajdujące się w innych kontenera. W przeciwnym razie są nierówne.

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

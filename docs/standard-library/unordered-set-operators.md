---
title: '&lt;unordered_set operatory&gt;'
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::operator!=
- unordered_set/std::operator==
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
ms.openlocfilehash: 59a7154ed46ac788516bc9f42c3385ec8f07dcf1
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422508"
---
# <a name="ltunordered_setgt-operators"></a>&lt;unordered_set operatory&gt;

## <a name="op_neq"></a>operator! =

Testuje, czy obiekt [unordered_set](../standard-library/unordered-set-class.md) po lewej stronie operatora nie jest równy obiektowi unordered_set po prawej stronie.

```cpp
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `unordered_set`.

*prawa*\
Obiekt typu `unordered_set`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli unordered_sets nie są równe; **Fałsz** , jeśli są równe.

### <a name="remarks"></a>Uwagi

Do porównania między obiektami unordered_set nie ma wpływ dowolne zamówienie, w którym są przechowywane elementy. Dwie unordered_sets są równe, jeśli mają taką samą liczbę elementów, a elementy w jednym kontenerze są Permutacją elementów w innym kontenerze. W przeciwnym razie są one nierówne.

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

**Rozdzielczości**

`c1 != c2: true`

`c1 != c3: false`

`c2 != c3: true`

## <a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt [unordered_set](../standard-library/unordered-set-class.md) po lewej stronie operatora jest równy obiektowi unordered_set po prawej stronie.

```cpp
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `unordered_set`.

*prawa*\
Obiekt typu `unordered_set`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli unordered_sets są równe; **wartość false** , jeśli nie są równe.

### <a name="remarks"></a>Uwagi

Do porównania między obiektami unordered_set nie ma wpływ dowolne zamówienie, w którym są przechowywane elementy. Dwie unordered_sets są równe, jeśli mają taką samą liczbę elementów, a elementy w jednym kontenerze są Permutacją elementów w innym kontenerze. W przeciwnym razie są one nierówne.

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

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```

## <a name="op_neq_unordered_multiset"></a>operator! =

Testuje, czy obiekt [unordered_multiset](../standard-library/unordered-multiset-class.md) po lewej stronie operatora nie jest równy obiektowi unordered_multiset po prawej stronie.

```cpp
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `unordered_multiset`.

*prawa*\
Obiekt typu `unordered_multiset`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli unordered_multisets nie są równe; **Fałsz** , jeśli są równe.

### <a name="remarks"></a>Uwagi

Do porównania między obiektami unordered_multiset nie ma wpływ dowolne zamówienie, w którym są przechowywane elementy. Dwie unordered_multisets są równe, jeśli mają taką samą liczbę elementów, a elementy w jednym kontenerze są Permutacją elementów w innym kontenerze. W przeciwnym razie są one nierówne.

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

```Output
c1 != c2: true
c1 != c3: false
c2 != c3: true
```

## <a name="op_eq_eq_unordered_multiset"></a>operator = =

Testuje, czy obiekt [unordered_multiset](../standard-library/unordered-multiset-class.md) po lewej stronie operatora jest równy obiektowi unordered_multiset po prawej stronie.

```cpp
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `unordered_multiset`.

*prawa*\
Obiekt typu `unordered_multiset`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli unordered_multisets są równe; **wartość false** , jeśli nie są równe.

### <a name="remarks"></a>Uwagi

Do porównania między obiektami unordered_multiset nie ma wpływ dowolne zamówienie, w którym są przechowywane elementy. Dwie unordered_multisets są równe, jeśli mają taką samą liczbę elementów, a elementy w jednym kontenerze są Permutacją elementów w innym kontenerze. W przeciwnym razie są one nierówne.

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

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```

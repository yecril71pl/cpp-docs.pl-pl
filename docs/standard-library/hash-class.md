---
title: hash — Klasa
ms.date: 11/04/2016
f1_keywords:
- functional/std::hash
- bitset/std::hash
- memory/std::hash
- string/std::hash
- system_error/std::hash
- thread/std::hash
- typeindex/std::hash
- vector/std::hash
- XSTDDEF/std::hash
- xstring/std::hash
helpviewer_keywords:
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
ms.assetid: e1b500c6-a5c8-4f6f-ad33-7ec52eb8e2e4
ms.openlocfilehash: e30810412db29473597da144d2dd42bdb8184f7e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688002"
---
# <a name="hash-class"></a>hash — Klasa

Oblicza kod skrótu dla wartości.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct hash {
    size_t operator()(Ty val) const;
};
```

## <a name="remarks"></a>Uwagi

Obiekt Function definiuje funkcję mieszania, odpowiednią do mapowania wartości typu *ty* na rozkład wartości indeksu. Element członkowski `operator()` zwraca kod skrótu dla wartości *Val*, odpowiedni do użycia z szablonami klas `unordered_map`, `unordered_multimap`, `unordered_set` i `unordered_multiset`. Biblioteka standardowa zawiera specjalizacje dla typów podstawowych: *ty* może być dowolnym typem skalarnym, w tym typami wskaźników i typami wyliczeniowymi. Ponadto istnieją specjalizacje dla typów bibliotek `string`, `wstring`, `u16string`, `u32string`, `string_view`, `wstring_view`, `u16string_view`, `u32string_view`, `bitset`, `error_code`, 0, 1, 2 , 3, 4, 5, 6 i 7.

## <a name="example"></a>Przykład

```cpp
// std__functional__hash.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <unordered_set>

int main()
    {
    std::unordered_set<int, std::hash<int> > c0;
    c0.insert(3);
    std::cout << *c0.find(3) << std::endl;

    return (0);
    }
```

```Output
3
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<functional >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< unordered_map >](../standard-library/unordered-map.md) \
[Klasa unordered_multimap](../standard-library/unordered-multimap-class.md) \
[Klasa unordered_multiset](../standard-library/unordered-multiset-class.md) \
[<unordered_set>](../standard-library/unordered-set.md)

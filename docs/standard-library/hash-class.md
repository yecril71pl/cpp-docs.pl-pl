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
ms.openlocfilehash: 61446ab6b79496024d44a99fcf5f500bb871bb80
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448819"
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

Obiekt Function definiuje funkcję mieszania, odpowiednią do mapowania wartości typu *ty* na rozkład wartości indeksu. Element członkowski `operator()` zwraca kod skrótu dla wartości *Val*, odpowiedni do użycia z klasami `unordered_map`szablonów `unordered_multimap`, `unordered_set`, i `unordered_multiset`. Biblioteka standardowa zawiera specjalizacje dla typów podstawowych: *Ty* może być dowolnego typu skalarnego, w tym typów wskaźnikowych i typów wyliczeniowych. Ponadto istnieją specjalizacje `string`dla typów bibliotek, `string_view` `u16string` `wstring` `u32string` ,`wstring_view` ,,`u32string_view`,, ,,,`bitset` `u16string_view` `error_code` `error_condition`, `optional`, ,,`shared_ptr`,, i`vector<bool>`. `thread` `type_index` `unique_ptr` `variant`

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

**Nagłówek:** \<> funkcjonalne

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<unordered_map>](../standard-library/unordered-map.md)\
[Klasa unordered_multimap](../standard-library/unordered-multimap-class.md)\
[Klasa unordered_multiset](../standard-library/unordered-multiset-class.md)\
[<unordered_set>](../standard-library/unordered-set.md)

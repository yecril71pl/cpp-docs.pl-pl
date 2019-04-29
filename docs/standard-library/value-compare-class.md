---
title: value_compare — Klasa
ms.date: 11/04/2016
f1_keywords:
- value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: 4b7fff1bef091a9d47e6ea4dc0e53e86ce39ad7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365292"
---
# <a name="valuecompare-class"></a>value_compare — Klasa

Dostarcza obiekt funkcji, która może porównać elementów hash_map przez porównanie wartości ich klucze, aby określić ich względną kolejność w hash_map.

## <a name="syntax"></a>Składnia

```cpp
class value_compare
    : std::public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(
        const value_type& left,
        const value_type& right) const
    {
        return (comp(left.first, right.first));
    }

protected:
    value_compare(const key_compare& c) : comp (c) { }
    key_compare comp;
};
```

## <a name="remarks"></a>Uwagi

Kryteria porównania, dostarczone przez value_compare między `value_types` całego elementów zawartych hash_map wywołane z porównania między kluczami elementów odpowiednich wynikające z konstrukcji klasy pomocniczej. Operator funkcji elementów członkowskich używa obiektu `comp` typu `key_compare` przechowywanych w obiekcie funkcji dostarczonych przez value_compare — Aby porównać składniki klucz sortowania w dwóch elementów.

Hash_sets i hash_multisets, które są proste kontenery, których wartości klucza są identyczne do wartości elementów, jest odpowiednikiem value_compare `key_compare`; hash_maps i hash_multimaps nie są one, ponieważ wartość typu `pair` elementy nie jest taka sama jak wartość klucza elementu.

## <a name="example"></a>Przykład

Zobacz przykład [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) przykładowy sposób deklarowania i użyj value_compare —.

## <a name="requirements"></a>Wymagania

**Header:** \<hash_map>

**Namespace:** stdext

## <a name="see-also"></a>Zobacz także

[binary_function, struktura](../standard-library/binary-function-struct.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>

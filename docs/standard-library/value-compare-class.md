---
title: value_compare — Klasa
ms.date: 11/04/2016
f1_keywords:
- value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: 0e057a6229c903402a51b34a8f4e844e80ace187
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452370"
---
# <a name="valuecompare-class"></a>value_compare — Klasa

Udostępnia obiekt funkcji, który może porównać elementy hash_map przez porównanie wartości ich kluczy w celu określenia ich względnej kolejności w hash_map.

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

Kryteria porównania dostarczone przez value_compare między `value_types` całymi elementami zawartymi w hash_map jest wywołane z porównania między kluczami odpowiednich elementów przez konstrukcję klasy pomocniczej. Operator funkcji składowej używa obiektu `comp` typu `key_compare` przechowywanego w obiekcie funkcji dostarczonym przez value_compare, aby porównać składniki klucza sortowania dwóch elementów.

W przypadku hash_sets i hash_multisets, które są prostymi kontenerami, w których wartości klucza są identyczne z wartościami elementu, value_compare `key_compare`jest równoważne; dla hash_maps i hash_multimaps nie są, ponieważ wartość typu `pair` elementy nie są identyczne z wartością klucza elementu.

## <a name="example"></a>Przykład

Zobacz przykład dla [hash_map:: value_comp](../standard-library/hash-map-class.md#value_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania value_compare.

## <a name="requirements"></a>Wymagania

**Header:** \<hash_map>

**Przestrzeń nazw:** stdext

## <a name="see-also"></a>Zobacz także

[binary_function, struktura](../standard-library/binary-function-struct.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

---
title: value_compare, Klasa&lt;(&gt;map)
ms.date: 11/04/2016
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
- value_compare
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
ms.openlocfilehash: d098e947aec1ea543f29c168a632d1f4c9412e82
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448325"
---
# <a name="valuecompare-class-ltmapgt"></a>value_compare, Klasa&lt;(&gt;map)

Udostępnia obiekt funkcji, który może porównać elementy mapy przez porównanie wartości ich kluczy w celu określenia ich względnej kolejności w mapie.

## <a name="syntax"></a>Składnia

```cpp
class value_compare : public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(const value_type& left, const value_type& right) const;
    value_compare(key_compare pred) : comp(pred);
protected:
    key_compare comp;
};
```

## <a name="remarks"></a>Uwagi

Kryterium porównania dostarczone przez `value_compare` między `value_types` całymi elementami zawartymi w mapie jest wywołane z porównania między kluczami odpowiednich elementów przez konstrukcję klasy pomocniczej. Operator funkcji składowej używa obiektu `comp` typu `key_compare` przechowywanego w obiekcie funkcji dostarczonym przez `value_compare` , aby porównać składniki klucza sortowania dwóch elementów.

Dla zestawów i zestawów wielozbiorów, które są prostymi kontenerami, w których wartości klucza są identyczne z `value_compare` wartościami elementu, `key_compare`są równoważne; w przypadku map i map wielowartościowych nie są, ponieważ wartość `pair` elementów typu nie jest taka sama jak wartość klucza elementu.

## <a name="example"></a>Przykład

Zobacz przykład dla [value_comp](../standard-library/map-class.md#value_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `value_compare`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<Mapuj >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[binary_function, struktura](../standard-library/binary-function-struct.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

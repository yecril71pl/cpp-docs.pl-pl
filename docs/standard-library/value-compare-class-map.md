---
title: Klasa value_compare (&lt;mapy&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
ms.openlocfilehash: 1f872edce6f0114be7c90a8108ba248fd793a989
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447583"
---
# <a name="value_compare-class-ltmapgt"></a>Klasa value_compare (&lt;mapy&gt;)

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

Kryterium porównania podane przez `value_compare` między `value_types` całkowitymi elementami zawartymi w mapie jest wywołane z porównania między kluczami odpowiednich elementów przez konstrukcję klasy pomocniczej. Operator funkcji składowej używa obiektu `comp` typu `key_compare` przechowywanego w obiekcie funkcji dostarczonym przez `value_compare`, aby porównać składniki klucza sortowania dwóch elementów.

Dla zestawów i wielozestawów, które są prostymi kontenerami, w których wartości klucza są identyczne z wartościami elementu, `value_compare` jest równoważne `key_compare`; w przypadku map i map wielodanych nie są, ponieważ wartość typu `pair` elementów nie jest taka sama jak wartość klucza elementu.

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [value_comp](../standard-library/map-class.md#value_comp) , aby zapoznać się z przykładem sposobu deklarowania i używania `value_compare`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mapowanie >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz też

[Binary_function struktura](../standard-library/binary-function-struct.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

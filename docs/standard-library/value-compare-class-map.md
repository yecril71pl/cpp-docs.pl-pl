---
title: value_compare — klasa (&lt;mapy&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
- value_compare
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
ms.openlocfilehash: 69b484944c9ce30dc28fceacfb082051da31c053
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365019"
---
# <a name="valuecompare-class-ltmapgt"></a>value_compare — klasa (&lt;mapy&gt;)

Dostarcza obiekt funkcji, która może porównać elementy mapy przez porównanie wartości ich kluczy, aby określić ich względną kolejność w mapie.

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

Kryterium porównania, dostarczone przez `value_compare` między `value_types` całego elementów zawartych w mapie wywołane z porównania między kluczami elementów odpowiednich wynikające z konstrukcji klasy pomocniczej. Operator funkcji elementów członkowskich używa obiektu `comp` typu `key_compare` przechowywanych w obiekcie funkcji dostarczonych przez `value_compare` do porównania składniki klucz sortowania w dwóch elementów.

Zestawów i multisets, będących kontenerami prosty, gdzie wartości klucza są identyczne do wartości elementów, `value_compare` jest odpowiednikiem `key_compare`; w przypadku map i multimaps są, jako wartość typu `pair` elementów nie jest taka sama jak wartość klucza elementu.

## <a name="example"></a>Przykład

Zobacz przykład dotyczący [value_comp —](../standard-library/map-class.md#value_comp) przykładowy sposób deklarowania i użyj `value_compare`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mapy >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[binary_function, struktura](../standard-library/binary-function-struct.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>

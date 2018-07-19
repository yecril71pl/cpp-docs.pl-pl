---
title: value_compare — klasa (&lt;mapy&gt;) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
- value_compare
dev_langs:
- C++
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 46f8d00877aa4147e4b3e4ec2a6a23b70d8154c8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965851"
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

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
ms.openlocfilehash: effa754f50f8c092cef727969a0f4036e765f888
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856049"
---
# <a name="valuecompare-class-ltmapgt"></a>value_compare — klasa (&lt;mapy&gt;)

Udostępnia obiekt funkcji, który można porównać elementów mapy porównując wartości ich kluczy, aby określić ich kolejność względne w planie.

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

Kryterium porównania dostarczonych przez `value_compare` między **value_types** elementów całego zawarty w mapie powstaniu porównanie między kluczami elementów odpowiednich przez konstrukcji klasy pomocniczej. Operator funkcji Członkowskich używa obiektu **kompozycji** typu `key_compare` przechowywane w dostarczony przez obiekt funkcja `value_compare` do porównania składniki klucza sortowania z dwóch elementów.

Zestawów i multisets, będących kontenerami proste, których wartości klucza są takie same jak wartości elementu, `value_compare` jest odpowiednikiem `key_compare`; map i nie są one jako wartość typu multimaps `pair` elementów nie jest taka sama jak wartość klucza elementu.

## <a name="example"></a>Przykład

Zobacz przykład [value_comp](../standard-library/map-class.md#value_comp) przykład sposobu deklarowanie i użycie `value_compare`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mapy >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[binary_function, struktura](../standard-library/binary-function-struct.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>

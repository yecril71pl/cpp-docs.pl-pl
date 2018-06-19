---
title: value_compare — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- value_compare
dev_langs:
- C++
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 594f3aaa45638ff2ab5d184a771070d87dbeb0bb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856586"
---
# <a name="valuecompare-class"></a>value_compare — Klasa

Udostępnia obiekt funkcji, który można porównać elementów hash_map porównując wartości ich kluczy, aby określić ich kolejność względne w hash_map.

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

Kryteriów porównania dostarczonych przez value_compare między **value_types** z całego zawartym hash_map powstaniu porównanie między kluczami elementów odpowiednich przez konstrukcji klasy pomocniczej. Operator funkcji Członkowskich używa obiektu **kompozycji** typu `key_compare` przechowywane w obiekcie funkcji dostarczonych przez value_compare do porównania składniki klucza sortowania z dwóch elementów.

Hash_sets i hash_multisets, będące proste kontenerów, których wartości klucza są takie same jak wartości elementów jest odpowiednikiem value_compare `key_compare`; hash_maps i hash_multimaps nie mają, ponieważ wartość typu `pair` elementy nie jest taka sama jak wartość klucza elementu.

## <a name="example"></a>Przykład

Zobacz przykład [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) przykład sposobu deklarowanie i użycie value_compare.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_map >

**Namespace:** stdext —

## <a name="see-also"></a>Zobacz także

[binary_function, struktura](../standard-library/binary-function-struct.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>

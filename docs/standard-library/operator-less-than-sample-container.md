---
title: operator&lt; (&lt;przykładowy kontener&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::operator<
- operator<
- std.<
- <
- std.operator<
- std::<
helpviewer_keywords:
- < operator, comparing specific objects
- operator<, valarrays
- < operator
- operator <, valarrays
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
ms.openlocfilehash: a286833d96e913a66240d25798e1cc230adf58b0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458724"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;przykładowy kontener&gt;)

> [!NOTE]
> Ten temat znajduje się w dokumentacji C++ firmy Microsoft jako przykład niefunkcjonalny kontenerów używanych w C++ standardowej bibliotece. Aby uzyskać więcej informacji, zobacz [ C++ Kontenery biblioteki standardowej](../standard-library/stl-containers.md).

**Operator przeciążenia <** do porównywania dwóch obiektów [kontenera](../standard-library/sample-container-class.md)klasy szablonu.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
bool operator<(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Wartość zwracana

Zwraca `lexicographical_compare(left.begin, left.end, right.begin, right.end)`wartość.

## <a name="see-also"></a>Zobacz także

[\<Przykładowy > kontenera](../standard-library/sample-container.md)\
[zaczną](../standard-library/container-class-begin.md)\
[punktów](../standard-library/container-class-end.md)
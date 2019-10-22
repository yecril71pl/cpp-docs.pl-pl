---
title: '&lt; operatora (&lt;sample kontenera &gt;)'
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
ms.openlocfilehash: fc2a14d882b5ccfbfdaae543c76ca673f9018a59
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687339"
---
# <a name="operatorlt-ltsample-containergt"></a>&lt; operatora (&lt;sample kontenera &gt;)

> [!NOTE]
> Ten temat znajduje się w dokumentacji C++ firmy Microsoft jako przykład niefunkcjonalny kontenerów używanych w C++ standardowej bibliotece. Aby uzyskać więcej informacji, zobacz [ C++ Kontenery biblioteki standardowej](../standard-library/stl-containers.md).

**Operator przeciążenia <** do porównywania dwóch obiektów [kontenera](../standard-library/sample-container-class.md)szablonu klasy.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
bool operator<(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Wartość zwracana

Zwraca `lexicographical_compare(left.begin, left.end, right.begin, right.end)`.

## <a name="see-also"></a>Zobacz także

[\<sample kontenera >](../standard-library/sample-container.md) \
[rozpocznij](../standard-library/container-class-begin.md) \
[punktów](../standard-library/container-class-end.md)
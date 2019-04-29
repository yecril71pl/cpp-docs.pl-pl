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
ms.openlocfilehash: 57796cc69dd734ea4c619db4bd8fedbfa09ce15b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371314"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;przykładowy kontener&gt;)

> [!NOTE]
> Ten temat dotyczy w dokumentacji języka Visual C++ jako prawidłowo przykład kontenerów używanych w standardowej biblioteki języka C++. Aby uzyskać więcej informacji, zobacz [standardowych kontenerów biblioteki języka C++](../standard-library/stl-containers.md).

Overloads **operatora <** do porównywania dwóch obiektów klasy szablonu [kontenera](../standard-library/sample-container-class.md).

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

[\<Przykładowy kontener >](../standard-library/sample-container.md)<br/>
[begin](../standard-library/container-class-begin.md)<br/>
[koniec](../standard-library/container-class-end.md)
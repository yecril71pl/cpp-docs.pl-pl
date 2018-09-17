---
title: operator&lt; (&lt;przykładowy kontener&gt;) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- std::operator<
- operator<
- std.<
- <
- std.operator<
- std::<
dev_langs:
- C++
helpviewer_keywords:
- < operator, comparing specific objects
- operator<, valarrays
- < operator
- operator <, valarrays
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd6e3343c4b0d64e16ce1d1a33d94ecaa7ef3fa5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713543"
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
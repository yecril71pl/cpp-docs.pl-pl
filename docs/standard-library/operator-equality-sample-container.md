---
title: operator = = (&lt;przykładowy kontener&gt;)
ms.date: 11/04/2016
f1_keywords:
- std.==
- std::==
- operator==
- std.operator==
- std::operator==
- ==
helpviewer_keywords:
- operator ==, containers
- operator==, containers
- == operator, with specific standard C++ objects
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
ms.openlocfilehash: 168785abb09ca198435c301040d7628a6dd12b26
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460152"
---
# <a name="operator-ltsample-containergt"></a>operator = = (&lt;przykładowy kontener&gt;)

> [!NOTE]
> Ten temat znajduje się w dokumentacji C++ firmy Microsoft jako przykład niefunkcjonalny kontenerów używanych w C++ standardowej bibliotece. Aby uzyskać więcej informacji, zobacz [ C++ Kontenery biblioteki standardowej](../standard-library/stl-containers.md).

Przeciążenia `operator==` do porównywania dwóch obiektów [kontenera](../standard-library/sample-container-class.md)klas szablonu.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Wartość zwracana

Zwraca `left.`[koniec](../standard-library/container-class-end.md) [](../standard-library/container-class-begin.md) [](../standard-library/container-class-size.md) ` == right.size && equal(left.`rozmiaru.`, left.``, right.begin)`

## <a name="see-also"></a>Zobacz także

[\<Przykładowy > kontenera](../standard-library/sample-container.md)

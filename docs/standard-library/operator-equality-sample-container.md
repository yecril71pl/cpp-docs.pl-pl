---
title: Operator == (&lt;przykładowy kontener&gt;)
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
ms.openlocfilehash: c49c58bdc168385d421cf942735b7473de70925f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613502"
---
# <a name="operator-ltsample-containergt"></a>Operator == (&lt;przykładowy kontener&gt;)

> [!NOTE]
> Ten temat dotyczy w dokumentacji języka Visual C++ jako prawidłowo przykład kontenerów używanych w standardowej biblioteki języka C++. Aby uzyskać więcej informacji, zobacz [standardowych kontenerów biblioteki języka C++](../standard-library/stl-containers.md).

Overloads `operator==` do porównywania dwóch obiektów klasy szablonu [kontenera](../standard-library/sample-container-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Wartość zwracana

Zwraca `left.` [rozmiar](../standard-library/container-class-size.md) ` == right.size && equal(left.` [rozpocząć](../standard-library/container-class-begin.md)`, left.`[zakończenia](../standard-library/container-class-end.md)`, right.begin)`.

## <a name="see-also"></a>Zobacz także

[\<Przykładowy kontener >](../standard-library/sample-container.md)<br/>

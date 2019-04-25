---
title: bool (C++)
ms.date: 11/04/2016
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
ms.openlocfilehash: e481cb9de7c80d147179efceab2fda9b160f3c21
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184289"
---
# <a name="bool-c"></a>bool (C++)

To słowo kluczowe jest typu wbudowanego. Zmienna tego typu może mieć wartości [true](../cpp/true-cpp.md) i [false](../cpp/false-cpp.md). Wyrażenia warunkowe mają typ **bool** i dlatego mają wartości typu **bool**. Na przykład `i!=0` ma teraz wartość PRAWDA lub FAŁSZ w zależności od wartości `i`.

**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): Argument przyrostka lub przedrostka inkrementacji lub dekrementacji operator nie może być typu **bool**. Innymi słowy, biorąc pod uwagę zmienną `b` typu **bool**, te wyrażenia nie są już dozwolone:

```cpp
    b++;
    ++b;
    b--;
    --b;
```

Wartości TRUE i FALSE mają następującą relację:

```cpp
!false == true
!true == false
```

W poniższej instrukcji:

```cpp
if (condexpr1) statement1;
```

Jeśli `condexpr1` ma wartość PRAWDA, `statement1` jest zawsze wykonywana; Jeśli `condexpr1` ma wartość FAŁSZ, `statement1` nigdy nie jest wykonywana.

Gdy przyrostka lub przedrostka **++** operator jest stosowany do zmiennej typu **bool**, zmienna jest ustawiana na wartość TRUE.
**Visual Studio 2017 w wersji 15.3 lub nowszej**: operator ++ dla **bool** został usunięty z języka i nie jest już obsługiwana.

Przyrostka lub przedrostka **--** do zmiennej tego typu nie można zastosować operatora.

**Bool** typ uczestniczy w promocjach integralnych. Wartości typu **bool** można przekonwertować wartości typu **int**z FALSE staje się zero i wartość TRUE, staje się jedynką. Jako typ samodzielny **bool** uczestniczy w przeciążeniu rozdzielczości.

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Typy podstawowe](../cpp/fundamental-types-cpp.md)
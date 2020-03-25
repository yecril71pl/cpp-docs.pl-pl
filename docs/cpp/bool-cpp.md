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
ms.openlocfilehash: db246cda79c778f37c5afbfda4a68c191c474e12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190498"
---
# <a name="bool-c"></a>bool (C++)

To słowo kluczowe jest typu wbudowanego. Zmienna tego typu może mieć wartości [true](../cpp/true-cpp.md) i [false](../cpp/false-cpp.md). Wyrażenia warunkowe mają typ **bool** i dlatego mają wartości typu **bool**. Na przykład `i!=0` ma teraz wartość TRUE lub FALSE, w zależności od wartości `i`.

**Program Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): argument operacji "przyrostka" przyrostkowego lub zmniejszania prefiksu nie może być typu **bool**. Innymi słowy, uwzględniając zmienną `b` typu **bool**, wyrażenia te nie są już dozwolone:

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

Jeśli `condexpr1` ma wartość TRUE, `statement1` jest zawsze wykonywane; Jeśli `condexpr1` ma wartość FALSE, `statement1` nigdy nie jest wykonywane.

Gdy operator przyrostka lub prefiks **++** jest stosowany do zmiennej typu **bool**, zmienna jest ustawiona na wartość true.
**Program Visual Studio 2017 w wersji 15,3 i nowszej**: operator + + dla elementu **bool** został usunięty z języka i nie jest już obsługiwany.

Nie można zastosować operatora przyrostka lub prefiksu **--** do zmiennej tego typu.

Typ **bool** uczestniczy w promocjach całkowitych. Wartość r typu **bool** może zostać przekonwertowana na wartość r typu **int**, przy czym wartość false staje się zerem i staje się jedną. Jako typ odrębny, **bool** uczestniczy w rozpoznaniu przeciążenia.

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Typy wbudowane](../cpp/fundamental-types-cpp.md)

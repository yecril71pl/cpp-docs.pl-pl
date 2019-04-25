---
title: Typy całkowite
ms.date: 11/04/2016
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
ms.openlocfilehash: 23da055b56e2ae77fed796d9ba8e7f227e572a9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232855"
---
# <a name="integer-types"></a>Typy całkowite

Każda stała całkowita posiada typ zależny od jej wartości i sposobu wyrażenia. Można wymusić dowolną stałą całkowitą na typ **długie** przez dołączenie litery **l** lub **L** na końcu stałej; można wymusić typ `unsigned` przez dołączenie **u** lub **U** wartość. Mała litera **l** może być pomylona z cyfrą 1 i należy ich unikać. Niektóre rodzaje **długie** stałych całkowitych:

```
/* Long decimal constants */
10L
79L

/* Long octal constants */
012L
0115L

/* Long hexadecimal constants */
0xaL or 0xAL
0X4fL or 0x4FL

/* Unsigned long decimal constant */
776745UL
778866LU
```

Typ przypisany do stałej zależy od wartości reprezentowanej przez stałą. Stała wartość musi być w zakresie reprezentowanych wartości dla tego typu. Typ stałej określa jakie konwersje są wykonywane, gdy stała jest używana w wyrażeniu lub znak minus (**-**) jest stosowany. Ta lista zawiera podsumowanie reguł konwersji dla stałych całkowitych.

- Typ stałej dziesiętnej bez sufiksu jest `int`, **long int**, lub **unsigned long int**. Pierwszy z tych trzech typów, w którym wartość stałej może być reprezentowana jest typem przypisanym do stałej.

- Typem przypisanym do stałych ósemkowych i szesnastkowych bez sufiksów jest `int`, `unsigned int`, **long int**, lub **unsigned long int** w zależności od wielkości stałej.

- Typem przypisanym do stałych z **u** lub **U** sufiks jest **unsigned int** lub **unsigned long int** w zależności od ich rozmiaru.

- Typem przypisanym do stałych z **l** lub **L** sufiks jest **long int** lub **unsigned long int** w zależności od ich rozmiaru.

- Typem przypisanym do stałych z **u** lub **U** i **l** lub **L** sufiks jest **unsigned long int**.

## <a name="see-also"></a>Zobacz także

[Stałe całkowite języka C](../c-language/c-integer-constants.md)

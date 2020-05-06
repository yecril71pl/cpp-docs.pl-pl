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

Każda stała całkowita posiada typ zależny od jej wartości i sposobu wyrażenia. Można wymusić dowolną stałą całkowitą typu **Long** , dołączając literę **l** lub **l** do końca stałej; można wymusić typ `unsigned` , dołączając **u** lub **u** do wartości. Mała litera **l** może być pomylona z cyfrą 1 i należy ją unikać. Niektóre formy **długich** stałych są następujące:

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

Typ przypisany do stałej zależy od wartości reprezentowanej przez stałą. Stała wartość musi być w zakresie reprezentowanych wartości dla tego typu. Typ stałej określa, które konwersje są wykonywane, gdy stała jest używana w wyrażeniu lub gdy jest stosowany znak minus (**-**). Ta lista zawiera podsumowanie reguł konwersji dla stałych całkowitych.

- Typ stałej dziesiętnej bez sufiksu to `int`, **long int**lub **unsigned long int**. Pierwszy z tych trzech typów, w których stała wartość może być reprezentowana, jest typem przypisanym do stałej.

- Typ przypisany do wartości ósemkowych i szesnastkowych bez sufiksów `int`to `unsigned int`,, **long int**lub **unsigned long int** w zależności od rozmiaru stałej.

- Typem przypisanym do stałych z sufiksem **u** lub **u** jest **unsigned int** lub **unsigned long int** w zależności od ich rozmiaru.

- Typem przypisanym do stałych z sufiksem **l** lub **l** jest **long int** lub **unsigned long int** w zależności od ich rozmiaru.

- Typem przypisanym do stałych z sufiksem **u** lub **u** i **l** lub **l** jest **unsigned long int**.

## <a name="see-also"></a>Zobacz też

[Stałe całkowite języka C](../c-language/c-integer-constants.md)

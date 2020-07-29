---
title: Typy całkowite
ms.date: 07/22/2020
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
ms.openlocfilehash: 61ed64c613bc88ed5bf62999ba77fa4090c1ec4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211804"
---
# <a name="integer-types"></a>Typy całkowite

Każda stała całkowita otrzymuje typ na podstawie jego wartości i sposobu jego wyrażania. Można wymusić dowolną stałą całkowitą do wpisania **`long`** przez dołączenie litery **`l`** lub **`L`** do końca stałej; można wymusić, aby można było wpisać **`unsigned`** wartość przez dołączenie **`u`** lub **`U`** do wartości. Małe litery **`l`** można mylić z cyfrą 1 i należy je unikać. Niektóre formy **`long`** stałych całkowitych są następujące:

```C
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

Typ przypisany do stałej zależy od wartości reprezentowanej przez stałą. Stała wartość musi być w zakresie reprezentowanych wartości dla tego typu. Typ stałej określa, które konwersje są wykonywane, gdy stała jest używana w wyrażeniu lub gdy jest stosowany znak minus ( **`-`** ). Ta lista zawiera podsumowanie reguł konwersji dla stałych całkowitych.

- Typem dla stałej dziesiętnej bez sufiksu jest **`int`** , **`long int`** , lub **`unsigned long int`** . Pierwszy z tych trzech typów, w których stała wartość może być reprezentowana, jest typem przypisanym do stałej.

- Typ przypisany do wartości ósemkowych i szesnastkowych bez sufiksów ma wartość **`int`** ,, **`unsigned int`** lub, **`long int`** **`unsigned long int`** w zależności od rozmiaru stałej.

- Typ przypisany do stałych z **`u`** **`U`** sufiksem lub jest **`unsigned int`** lub **`unsigned long int`** zależny od ich rozmiaru.

- Typ przypisany do stałych z **`l`** **`L`** sufiksem or jest **`long int`** lub **`unsigned long int`** zależny od ich rozmiaru.

- Typ przypisany do stałych z **`u`** **`U`** **`l`** sufiksem lub i lub **`L`** jest **`unsigned long int`** .

## <a name="see-also"></a>Zobacz także

[Stałe całkowite języka C](../c-language/c-integer-constants.md)

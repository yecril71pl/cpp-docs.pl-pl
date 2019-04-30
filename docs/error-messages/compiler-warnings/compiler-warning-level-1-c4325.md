---
title: Kompilator ostrzeżenie (poziom 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 293cbbcfe134f6cb4f5e1bf924be7c03fa278833
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408540"
---
# <a name="compiler-warning-level-1-c4325"></a>Kompilator ostrzeżenie (poziom 1) C4325

> atrybuty dla standardowej sekcji "*sekcji*" zignorowany

## <a name="remarks"></a>Uwagi

Nie możesz zmienić atrybuty standardowej sekcji. Na przykład:

```cpp
#pragma section(".sdata", long)
```

To spowodowałoby zastąpienie `.sdata` standardowa sekcja, która używa **krótki** to typ danych **długie** typu danych.

Standardowa sekcje zawierają atrybuty, których nie można zmienić,

- .data

- .sdata

- .BSS

- .sbss

- .Text

- .const

- .sconst

- .rdata

- .srdata

Dodatkowe sekcje mogą być dodawane później.

## <a name="see-also"></a>Zobacz także

[sekcja](../../preprocessor/section.md)
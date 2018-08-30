---
title: Kompilator ostrzeżenie (poziom 1) C4325 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd265938afb51cc402dc84f38b7e95188c6292a7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197488"
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

- .Data

- .sdata

- .BSS

- .sbss

- .Text

- .const —

- .sconst

- .rdata

- .srdata

Dodatkowe sekcje mogą być dodawane później.

## <a name="see-also"></a>Zobacz także

[sekcja](../../preprocessor/section.md)
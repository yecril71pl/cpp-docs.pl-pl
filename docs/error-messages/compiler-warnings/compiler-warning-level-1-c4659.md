---
title: Kompilator ostrzeżenie (poziom 1) C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 2aef25e922d8f38ac7103b1b12ccb31c282f0403
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443473"
---
# <a name="compiler-warning-level-1-c4659"></a>Kompilator ostrzeżenie (poziom 1) C4659

\#pragma "dyrektywy": użycie zastrzeżonego segmentu "segmentu" ma niezdefiniowane zachowanie, użyj #pragma komentarz (konsolidator,...)

Opcja .drectve zostało użyte do przekazywania opcji do konsolidatora. Zamiast tego użyć pragma [komentarz](../../preprocessor/comment-c-cpp.md) przekazywania opcji konsolidatora.

```
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```
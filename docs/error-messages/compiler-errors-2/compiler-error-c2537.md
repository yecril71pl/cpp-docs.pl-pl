---
title: Błąd kompilatora C2537
ms.date: 11/04/2016
f1_keywords:
- C2537
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
ms.openlocfilehash: 437727b334087aef496dbb0a1f3f1c8cf2b45458
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492676"
---
# <a name="compiler-error-c2537"></a>Błąd kompilatora C2537

"specyfikatora": Niedozwolona specyfikacja powiązania

Możliwe przyczyny:

1. Specyfikator powiązania nie jest obsługiwane. Obsługiwane jest tylko specyfikator powiązania "C".

1. Powiązania "C" określono więcej niż jedną funkcję w zestaw przeciążonych funkcji. Jest to niedozwolone.

Poniższy przykład spowoduje wygenerowanie C2537:

```
// C2537.cpp
// compile with: /c
extern "c" void func();   // C2537
extern "C" void func2();   // OK
```
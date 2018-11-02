---
title: Błąd kompilatora C2598
ms.date: 11/04/2016
f1_keywords:
- C2598
helpviewer_keywords:
- C2598
ms.assetid: 40777c62-39ba-441e-b081-f49f94b43547
ms.openlocfilehash: 521a67bdf1e1f64853a3f87933b3fa714c8e33f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578233"
---
# <a name="compiler-error-c2598"></a>Błąd kompilatora C2598

Specyfikacja konsolidacji musi znajdować się w zakresie globalnym

Specyfikator powiązania jest zadeklarowana w zakresie lokalnym.

Poniższy przykład spowoduje wygenerowanie C2598:

```
// C2598.cpp
// compile with: /c
void func() {
   extern "C" int func2();   // C2598
}

extern "C" int func( int i );
```
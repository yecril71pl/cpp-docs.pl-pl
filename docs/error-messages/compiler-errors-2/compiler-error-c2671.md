---
title: Błąd kompilatora C2671
ms.date: 11/04/2016
f1_keywords:
- C2671
helpviewer_keywords:
- C2671
ms.assetid: fc0ee40f-c8f3-408f-b89d-745d149c4169
ms.openlocfilehash: 92ed646b0e4c5d2bbc6556c2a7b1ef66d8192ec1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496034"
---
# <a name="compiler-error-c2671"></a>Błąd kompilatora C2671

'Funkcja': statyczne funkcje Członkowskie nie mają wskaźników "this"

A `static` funkcja elementu członkowskiego próbował uzyskać dostęp do `this`.

Poniższy przykład spowoduje wygenerowanie C2671:

```
// C2671.cpp
struct S {
   static S* const func() { return this; }  // C2671
};
```
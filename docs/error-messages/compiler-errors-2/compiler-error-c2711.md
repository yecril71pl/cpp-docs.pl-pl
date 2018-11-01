---
title: Błąd kompilatora C2711
ms.date: 11/04/2016
f1_keywords:
- C2711
helpviewer_keywords:
- C2711
ms.assetid: 9df9f808-7419-4e63-abdd-e6538ff0871f
ms.openlocfilehash: 568128d6199d16380b6a540173eded25f5588d23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571850"
---
# <a name="compiler-error-c2711"></a>Błąd kompilatora C2711

'Funkcja': Ta funkcja nie może być skompilowana jako zarządzana, należy rozważyć użycie niezarządzanej funkcji #pragma

Dodatkowe instrukcje uniemożliwi kompilatorowi Generowanie MSIL dla funkcji otaczającej.

Poniższy przykład spowoduje wygenerowanie C2711:

```
// C2711.cpp
// compile with: /clr
// processor: x86
using namespace System;
value struct V {
   static const t = 10;
};

void bar() {
   V::t;
   __asm int 3   // C2711 inline asm can't be compiled managed
}
```
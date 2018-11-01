---
title: Błąd kompilatora C2556
ms.date: 11/04/2016
f1_keywords:
- C2556
helpviewer_keywords:
- C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
ms.openlocfilehash: 4a2b4dc9dcd71d518845651dee97c566b778eb0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484152"
---
# <a name="compiler-error-c2556"></a>Błąd kompilatora C2556

'Identyfikator': przeciążonych funkcji różnią się tylko typem zwracanym

Przeciążone funkcje mają różne typy zwracane, ale tę samą listę parametrów. Każdy przeciążonej funkcji musi mieć różne formalnej listy parametrów.

Poniższy przykład spowoduje wygenerowanie C2556:

```
// C2556.cpp
// compile with: /c
class C {
   int func();
   double func();   // C2556
   int func(int i);   // ok parameter lists differ
};
```
---
title: Błąd kompilatora C2706
ms.date: 11/04/2016
f1_keywords:
- C2706
helpviewer_keywords:
- C2706
ms.assetid: e18da924-c42d-4b09-8e29-f4e0382d7dc6
ms.openlocfilehash: 9767d36d44b99423d600d299d0803901d3dbfec5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472517"
---
# <a name="compiler-error-c2706"></a>Błąd kompilatora C2706

niedozwolone __except bez dopasowania \__try (Brak "}" w \_bloku _try?)

Kompilator nie znaleziono zamykającego nawiasu klamrowego dla `__try` bloku.

Poniższy przykład spowoduje wygenerowanie C2706:

```
// C2706.cpp
int main() {
   __try {
      void f();
   // C2706  } missing here
   __except(GetExceptionCode() == 0x0) {
   }
}
```
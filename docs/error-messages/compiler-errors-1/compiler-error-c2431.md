---
title: Błąd kompilatora C2431
ms.date: 11/04/2016
f1_keywords:
- C2431
helpviewer_keywords:
- C2431
ms.assetid: 88a5b648-c89f-47d1-a20e-63231ab4f0f7
ms.openlocfilehash: 6298748b341d58c5d931566f714530a4858e46ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608107"
---
# <a name="compiler-error-c2431"></a>Błąd kompilatora C2431

Niedozwolony indeks rejestru w 'Identyfikator'

Zarejestruj ESP jest skalowany lub używany zarówno jako index i zarejestruj podstawowej. RODZEŃSTWA, kodowanie x86 nie zezwala na jeden procesor.

Poniższy przykład spowoduje wygenerowanie C2431:

```
// C2431.cpp
// processor: x86
int main() {
   _asm mov ax, [ESI + 2*ESP]   // C2431
   _asm mov ax, [esp + esp]   // C2431
}
```
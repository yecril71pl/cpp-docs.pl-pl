---
title: Błąd kompilatora C2431 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2431
dev_langs:
- C++
helpviewer_keywords:
- C2431
ms.assetid: 88a5b648-c89f-47d1-a20e-63231ab4f0f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 944bead5439abf686fd18e436664e3c1cf7bccb5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049961"
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
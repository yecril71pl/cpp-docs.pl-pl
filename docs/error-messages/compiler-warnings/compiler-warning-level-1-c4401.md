---
title: Kompilator ostrzeżenie (poziom 1) C4401 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4401
dev_langs:
- C++
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f9f7bfcf826b9bda4232a8f4068d8be45dc3ab5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043550"
---
# <a name="compiler-warning-level-1-c4401"></a>Kompilator ostrzeżenie (poziom 1) C4401

"bitfield": składowa jest polem bitowym

Wbudowany kod asemblera próbuje uzyskać dostępu do członka pole bitowe. Wbudowany zestaw nie ma dostępu członków pola bitowego, więc ostatniego granicy pakowania przed składowej pola bitowego jest używany.

Aby uniknąć tego ostrzeżenia, należy zrzutować pola bitowego do odpowiedniego typu przed wprowadzeniem odwołania w kodzie zestawu wbudowanego. Poniższy przykład spowoduje wygenerowanie C4401:

```
// C4401.cpp
// compile with: /W1
// processor: x86
typedef struct bitfield {
   signed bit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bf.bit = 0;
   __asm {
      mov bf.bit,0;   // C4401
   }

   /* use the following __asm block to resolve the warning
   int i = (int)bf.bit;
   __asm {
      mov i,0;
   }
   */
}
```
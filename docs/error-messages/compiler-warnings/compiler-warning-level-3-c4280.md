---
title: Kompilator ostrzeżenie (poziom 3) C4280
ms.date: 11/04/2016
f1_keywords:
- C4280
helpviewer_keywords:
- C4280
ms.assetid: 153fb639-3ee1-4fee-baf9-71420abcf3f6
ms.openlocfilehash: 6a3daa9903cbf983ddc19538a154d9717a2f9f0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618936"
---
# <a name="compiler-warning-level-3-c4280"></a>Kompilator ostrzeżenie (poziom 3) C4280

"operator ->" był Auto rekurencyjny za pośrednictwem typu "type"

Twój kod niepoprawnie umożliwia **operator ->** można wywoływać samego siebie.

Poniższy przykład spowoduje wygenerowanie C4280:

```
// C4280.cpp
// compile with: /W3 /WX
struct A
{
   int z;
   A& operator ->();
};

void f(A y)
{
   int i = y->z; // C4280
}
```
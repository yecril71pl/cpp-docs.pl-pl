---
title: Kompilator ostrzeżenie (poziom 1) C4333
ms.date: 11/04/2016
f1_keywords:
- C4333
helpviewer_keywords:
- C4333
ms.assetid: d3763c52-6110-4da0-84db-5264e3f3f166
ms.openlocfilehash: b0f87b5d839dcfbb577af567a1a51a95daf716f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557355"
---
# <a name="compiler-warning-level-1-c4333"></a>Kompilator ostrzeżenie (poziom 1) C4333

'operator': przesunięcie w prawo o zbyt dużą liczbę, utrata danych

Operacja przesunięcia bitowego w prawo była zbyt duża.  Wszystkie znaczące bity są przesuwane w poziomie, a wynik będzie zawsze zero.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4333.

```
// C4333.cpp
// compile with: /c /W1
unsigned shift8 (unsigned char c) {
   return c >> 8;   // C4333

   // try the following line instead
   // return c >> 4;   // OK
}
```
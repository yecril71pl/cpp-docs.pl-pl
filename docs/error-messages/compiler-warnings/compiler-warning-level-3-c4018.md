---
title: Kompilator ostrzeżenie (poziom 3) C4018
ms.date: 11/04/2016
f1_keywords:
- C4018
helpviewer_keywords:
- C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
ms.openlocfilehash: 6436f62a06cbe931ca5b42751d60507f21675c5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556549"
---
# <a name="compiler-warning-level-3-c4018"></a>Kompilator ostrzeżenie (poziom 3) C4018

"expression": niezgodność ze znakiem/bez znaku

Porównywanie ze znakiem i bez znaku liczby wymagany kompilator, aby przekonwertować wartość ze znakiem na typy bez znaku.

To ostrzeżenie, mogą zostać rozwiązane, jeśli możesz oddać jeden z dwóch typów podczas testowania typami ze znakiem i bez znaku.

Poniższy przykład spowoduje wygenerowanie C4018:

```
// C4018.cpp
// compile with: /W3
int main() {
   unsigned int uc = 0;
   int c = 0;
   unsigned int c2 = 0;

   if (uc < c) uc = 0;   // C4018

   // OK
   if (uc == c2) uc = 0;
}
```
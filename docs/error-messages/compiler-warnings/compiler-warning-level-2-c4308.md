---
title: Kompilator ostrzeżenie (poziom 2) C4308
ms.date: 11/04/2016
f1_keywords:
- C4308
helpviewer_keywords:
- C4308
ms.assetid: d4e5c53c-71b2-4bbc-8a7c-3a2a3180d9d9
ms.openlocfilehash: f97d66f9e3445d022adc3362532774b15ea09961
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443540"
---
# <a name="compiler-warning-level-2-c4308"></a>Kompilator ostrzeżenie (poziom 2) C4308

ujemne stałe całkowite skonwertowano na typ bez znaku

Wyrażenie konwertuje stałą ujemną liczbę całkowitą na typ bez znaku. Wynikiem wyrażenia jest prawdopodobnie ta nie ma znaczenia.

## <a name="example"></a>Przykład

```
// C4308.cpp
// compile with: /W2
unsigned int u = (-5 + 3U);   // C4308

int main()
{
}
```
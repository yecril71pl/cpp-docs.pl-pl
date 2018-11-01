---
title: Kompilator ostrzeżenie (poziom 1) C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: af091d1d35fff955afcc5af3da48b80416e79f36
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485637"
---
# <a name="compiler-warning-level-1-c4731"></a>Kompilator ostrzeżenie (poziom 1) C4731

"wskaźnik": rejestr wskaźnika "register" zmodyfikowany przez wbudowany kod asemblera ramki

Rejestr wskaźnika ramki zostało zmodyfikowane. Należy zapisać i przywrócić rejestr w tekście zestawu bloku lub ramki zmiennej (lokalnego lub parametru, w zależności od rejestru modyfikacji) lub Twój kod może nie działać prawidłowo.

Poniższy przykład spowoduje wygenerowanie C4731:

```
// C4731.cpp
// compile with: /W1 /LD
// processor: x86
// C4731 expected
void bad(int p) {
   __asm
   {
      mov ebp, 1
   }

   if (p == 1)
   {
      // ...
   }
}
```

EBP jest wskaźnik ramki (niedopuszczalne FPO) i jest modyfikowana. Gdy `p` jest późniejsza odwołania, jest ona przywoływana względem `EBP`. Ale `EBP` został zastąpiony przez kod, dzięki czemu program nie będzie działać prawidłowo i może nawet błędów.
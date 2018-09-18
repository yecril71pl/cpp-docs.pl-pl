---
title: Kompilator ostrzeżenie (poziom 1) C4731 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4731
dev_langs:
- C++
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75117b34e63694cfa6aeec97abf178ff8e61a7da
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086489"
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
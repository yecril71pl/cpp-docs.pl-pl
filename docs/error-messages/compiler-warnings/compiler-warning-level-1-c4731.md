---
title: Ostrzeżenie kompilatora (poziom 1) C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: b2591756dfaa8887affbe4e470f1c98738b6b680
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052429"
---
# <a name="compiler-warning-level-1-c4731"></a>Ostrzeżenie kompilatora (poziom 1) C4731

"wskaźnik": Rejestr wskaźnika ramki "Register" został zmodyfikowany przez wbudowany kod asemblera

Zmodyfikowano rejestr wskaźników klatki. Musisz zapisać i przywrócić rejestr w bloku zestawu wbudowanego lub zmiennej ramki (Local lub Parameter, w zależności od zmodyfikowanego rejestru) lub kod może nie funkcjonować prawidłowo.

Poniższy przykład generuje C4731:

```cpp
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

EBP jest wskaźnikiem ramki (FPO jest niedozwolony) i jest modyfikowany. Gdy `p` jest przywoływany, odwołuje się względem `EBP`. Ale `EBP` został nadpisany przez kod, więc program nie będzie działał prawidłowo i może nawet ulec awarii.
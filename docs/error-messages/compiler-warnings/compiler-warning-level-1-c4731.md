---
title: Ostrzeżenie kompilatora (poziom 1) C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: 72483b734a1463b7b211c49ef21a01536ffa0ea1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185727"
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

---
title: Błąd kompilatora C2647
ms.date: 11/04/2016
f1_keywords:
- C2647
helpviewer_keywords:
- C2647
ms.assetid: 1034589e-bc3e-41a6-831f-2a1a4b8a2500
ms.openlocfilehash: 9553c85efeedb4d3eee4bd40f9e3b86707fd7eb1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758388"
---
# <a name="compiler-error-c2647"></a>Błąd kompilatora C2647

"operator": nie można usunąć odwołania do elementu "type1" w "type2"

Nie można niejawnie przekonwertować operandu lewego operatora wskaźnika do elementu członkowskiego (`->*` lub `.*`) na typ powiązany z operatorem praw.

Poniższy przykład generuje C2647:

```cpp
// C2647.cpp
class C {};
class D {};

int main() {
   D d, *pd;
   C c, *pc = 0;
   int C::*pmc = 0;
   pd->*pmc = 0;   // C2647
   d.*pmc = 0;   // C2647

   // OK
   pc->*pmc = 0;
   c.*pmc = 0;
}
```

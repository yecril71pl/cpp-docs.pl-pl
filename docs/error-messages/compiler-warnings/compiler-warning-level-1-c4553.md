---
title: Ostrzeżenie kompilatora (poziom 1) C4553
ms.date: 11/04/2016
f1_keywords:
- C4553
helpviewer_keywords:
- C4553
ms.assetid: d8aacbe0-3cb5-4367-a6e5-fd7e28f0ff9d
ms.openlocfilehash: a2d5e52e565878011b2439792c721eeb57cdd20a
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966327"
---
# <a name="compiler-warning-level-1-c4553"></a>Ostrzeżenie kompilatora (poziom 1) C4553

"operator": operator nie ma żadnego wpływu; Czy chodziło o "operator"?

Jeśli instrukcja wyrażenia ma operator bez efektów ubocznych w górnej części wyrażenia, prawdopodobnie wystąpi błąd.

Poniższy przykład generuje C4553:

```cpp
// C4553.cpp
// compile with: /W1
int func()
{
   return 0;
}

int main()
{
   int i;
   i == func();   // C4553
   // try the following line instead
   // i = func();
}
```
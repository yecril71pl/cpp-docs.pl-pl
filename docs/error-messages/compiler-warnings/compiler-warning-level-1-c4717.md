---
title: Ostrzeżenie kompilatora (poziom 1) C4717
ms.date: 11/04/2016
f1_keywords:
- C4717
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
ms.openlocfilehash: 0bc95cc770914a1c02a7a40f9754415c2f013d63
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051346"
---
# <a name="compiler-warning-level-1-c4717"></a>Ostrzeżenie kompilatora (poziom 1) C4717

"Function": rekursywnie we wszystkich ścieżkach kontroli, funkcja spowoduje przepełnienie stosu środowiska uruchomieniowego

Każda ścieżka przez funkcję zawiera wywołanie funkcji. Ponieważ nie istnieje sposób, aby wyjść z funkcji bez uprzedniego wywołania się cyklicznie, funkcja nigdy nie zostanie zakończona.

Poniższy przykład generuje C4717:

```cpp
// C4717.cpp
// compile with: /W1 /c
// C4717 expected
int func(int x) {
   if (x > 1)
      return func(x - 1); // recursive call
   else {
      int y = func(0) + 1; // recursive call
      return y;
   }
}

int main(){
   func(1);
}
```
---
title: Błąd kompilatora C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: 8350c5baf129b88c178be280d2da7fe856c6cf57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517614"
---
# <a name="compiler-error-c2561"></a>Błąd kompilatora C2561

'Identyfikator': funkcja musi zwracać wartość

Funkcja została zadeklarowana jako zwracanie wartości, ale nie zawiera definicji funkcji `return` instrukcji.

Ten błąd może być spowodowany przez prototypu funkcji niepoprawne:

1. Jeśli funkcja nie zwraca wartości, Zadeklaruj funkcję z typem zwracanym [void](../../cpp/void-cpp.md).

1. Upewnij się, że wszystkie możliwe gałęzie funkcji zwrócić wartość typem zadeklarowanym w prototypie.

1. Funkcje języka C++, zawierające wbudowanego zestawu procedur, które będą przechowywać wartość zwracaną w `AX` rejestru może być konieczne instrukcji return. Skopiuj wartość w `AX` do zmiennej tymczasowej i zwraca tę zmienną z funkcji.

Poniższy przykład spowoduje wygenerowanie C2561:

```
// C2561.cpp
int Test(int x) {
   if (x) {
      return;   // C2561
      // try the following line instead
      // return 1;
   }
   return 0;
}

int main() {
   Test(1);
}
```
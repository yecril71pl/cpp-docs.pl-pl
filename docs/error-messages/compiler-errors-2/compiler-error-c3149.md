---
title: Błąd kompilatora C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 8238dcec821256dad8101cd7ad59b2d85882c218
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345515"
---
# <a name="compiler-error-c3149"></a>Błąd kompilatora C3149

"type": nie można użyć tego typu, w tym miejscu bez najwyższego poziomu "char"

Deklaracja nie został poprawnie określony.

Na przykład możesz mieć zdefiniowane typu CLR w zakresie globalnym i nastąpiła próba utworzenia zmiennej typu jako część definicji. Ponieważ zmienne globalne, typy CLR nie są dozwolone, kompilator wygeneruje C3149.

Aby rozwiązać ten problem, należy zadeklarować zmienne typy CLR wewnątrz definicji funkcji lub typu.

Poniższy przykład spowoduje wygenerowanie C3149:

```
// C3149.cpp
// compile with: /clr
using namespace System;
int main() {
   // declare an array of value types
   array< Int32 ^> IntArray;   // C3149
   array< Int32>^ IntArray2;   // OK
}
```

Poniższy przykład spowoduje wygenerowanie C3149:

```
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```

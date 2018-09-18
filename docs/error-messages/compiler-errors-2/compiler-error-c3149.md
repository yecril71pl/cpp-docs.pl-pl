---
title: Błąd kompilatora C3149 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3149
dev_langs:
- C++
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a522bfd3ba236661f206d8d4e4b550179c06b3f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033124"
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

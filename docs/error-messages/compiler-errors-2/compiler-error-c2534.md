---
title: Błąd kompilatora C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: e684804ea31b16f31c82e244cb4f9a6aaf2d08c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386970"
---
# <a name="compiler-error-c2534"></a>Błąd kompilatora C2534

"identyfikator": Konstruktor nie może zwracać wartości

Konstruktor nie może zwracać wartości lub typem zwracanym (nie jest jeszcze `void` zwracany typ).

Ten błąd może zostać naprawione przez usunięcie `return` instrukcji z definicji konstruktora.

Poniższy przykład spowoduje wygenerowanie C2534:

```
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```
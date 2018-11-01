---
title: Błąd kompilatora C2553
ms.date: 11/04/2016
f1_keywords:
- C2553
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
ms.openlocfilehash: 11cb2b83d958f0c59d05034a716a022f00b326ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658682"
---
# <a name="compiler-error-c2553"></a>Błąd kompilatora C2553

"base_function": przesłanianie wirtualnej funkcji zwraca typ różni się od "override_function"

Funkcja w klasie pochodnej próbował zastępują funkcję wirtualną w klasie bazowej, ale funkcja klasy pochodnej nie miał taki sam zwracany typ funkcji klasy podstawowej.  Sygnatura funkcji zastąpienie musi odpowiadać podpisowi przesłaniana funkcja.

Poniższy przykład spowoduje wygenerowanie C2553:

```
// C2553.cpp
// compile with: /clr /c
ref struct C {
   virtual void f();
};

ref struct D : C {
   virtual int f() override ;   // C2553

   // try the following line instead
   // virtual void f() override;
};
```
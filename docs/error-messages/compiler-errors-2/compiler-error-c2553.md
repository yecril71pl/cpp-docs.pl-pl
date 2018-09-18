---
title: Błąd kompilatora C2553 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2553
dev_langs:
- C++
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38fb61b7281dd0371c546fd7b7bc960232cf2e00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043992"
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
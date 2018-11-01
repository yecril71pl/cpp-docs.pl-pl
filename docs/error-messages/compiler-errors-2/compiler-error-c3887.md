---
title: Błąd kompilatora C3887
ms.date: 11/04/2016
f1_keywords:
- C3887
helpviewer_keywords:
- C3887
ms.assetid: a7e82426-ef99-437b-9562-2822004e18fe
ms.openlocfilehash: e41ea1dbe1f2bd47f9b557d502ec95bcecb1e2a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428266"
---
# <a name="compiler-error-c3887"></a>Błąd kompilatora C3887

"var": Inicjator literału składowej danych musi być wyrażeniem stałym

A [literału](../../windows/literal-cpp-component-extensions.md) element członkowski danych może zostać zainicjowana tylko z wyrażeniem stałej.

Poniższy przykład spowoduje wygenerowanie C3887:

```
// C3887.cpp
// compile with: /clr
ref struct Y1 {
   static int i = 9;
   literal
   int staticConst = i;   // C3887
};
```

Możliwe rozwiązanie:

```
// C3887b.cpp
// compile with: /clr /c
ref struct Y1 {
   literal
   int staticConst = 9;
};
```
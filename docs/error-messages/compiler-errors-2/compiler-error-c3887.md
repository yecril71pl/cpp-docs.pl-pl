---
title: Błąd kompilatora C3887
ms.date: 11/04/2016
f1_keywords:
- C3887
helpviewer_keywords:
- C3887
ms.assetid: a7e82426-ef99-437b-9562-2822004e18fe
ms.openlocfilehash: 85434cb8daba0db82843c09e2d1bb09d98960272
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779050"
---
# <a name="compiler-error-c3887"></a>Błąd kompilatora C3887

"var": Inicjator literału składowej danych musi być wyrażeniem stałym

A [literału](../../extensions/literal-cpp-component-extensions.md) element członkowski danych może zostać zainicjowana tylko z wyrażeniem stałej.

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
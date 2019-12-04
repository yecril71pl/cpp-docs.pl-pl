---
title: Błąd kompilatora C3887
ms.date: 11/04/2016
f1_keywords:
- C3887
helpviewer_keywords:
- C3887
ms.assetid: a7e82426-ef99-437b-9562-2822004e18fe
ms.openlocfilehash: f64b72fe5d546550c32f60a27360d8a77c8255bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736584"
---
# <a name="compiler-error-c3887"></a>Błąd kompilatora C3887

"var": inicjator literału składowej danych musi być wyrażeniem stałym

[Literał](../../extensions/literal-cpp-component-extensions.md) składowej danych może być zainicjowany tylko przy użyciu stałej expresion.

Poniższy przykład generuje C3887:

```cpp
// C3887.cpp
// compile with: /clr
ref struct Y1 {
   static int i = 9;
   literal
   int staticConst = i;   // C3887
};
```

Możliwe rozwiązanie:

```cpp
// C3887b.cpp
// compile with: /clr /c
ref struct Y1 {
   literal
   int staticConst = 9;
};
```

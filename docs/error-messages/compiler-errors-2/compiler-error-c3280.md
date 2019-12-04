---
title: Błąd kompilatora C3280
ms.date: 11/04/2016
f1_keywords:
- C3280
helpviewer_keywords:
- C3280
ms.assetid: 86dc5bbc-8818-4786-a728-9334268d308b
ms.openlocfilehash: 127ff9d56f48ad276a59fba984deba16f2f8c339
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757595"
---
# <a name="compiler-error-c3280"></a>Błąd kompilatora C3280

"Class": funkcji składowej typu zarządzanego nie można skompilować jako funkcji niezarządzanej

Funkcji składowych klasy zarządzanej nie można kompilować jako funkcji niezarządzanych.

Poniższy przykład generuje C3280:

```cpp
// C3280_2.cpp
// compile with: /clr
ref struct A {
   void func();
};

#pragma managed(push,off)

void A::func()   // C3280
{
}

#pragma managed(pop)
```

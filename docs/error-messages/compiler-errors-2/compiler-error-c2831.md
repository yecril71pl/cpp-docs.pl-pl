---
title: Błąd kompilatora C2831
ms.date: 11/04/2016
f1_keywords:
- C2831
helpviewer_keywords:
- C2831
ms.assetid: c8c04288-0889-4265-a077-17f94cbcdcc9
ms.openlocfilehash: d2fa97e4b293d306a7d6ceecd08256c8212f8cb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736896"
---
# <a name="compiler-error-c2831"></a>Błąd kompilatora C2831

"operator operatora" nie może mieć parametrów domyślnych

Tylko trzy operatory mogą mieć domyślne parametry:

- [new](../../cpp/new-operator-cpp.md)

- Przypisanie =

- Lewy nawias okrągły (

Poniższy przykład generuje C2831:

```cpp
// C2831.cpp
// compile with: /c
#define BINOP <=
class A {
public:
   int i;
   int operator BINOP(int x = 1) {   // C2831
   // try the following line instead
   // int operator BINOP(int x) {
      return i+x;
   }
};
```

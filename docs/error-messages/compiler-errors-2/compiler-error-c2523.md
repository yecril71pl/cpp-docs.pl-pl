---
title: Błąd kompilatora C2523
ms.date: 11/04/2016
f1_keywords:
- C2523
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
ms.openlocfilehash: 56b0f88949d7a7fa5af945ab5d03ee9a480d6d3f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746425"
---
# <a name="compiler-error-c2523"></a>Błąd kompilatora C2523

"Class:: ~ identifier": niezgodność tagów destruktora/finalizatora

Nazwa destruktora musi być nazwą klasy poprzedzoną tyldą (`~`). Konstruktor i destruktor są jedynymi elementami członkowskimi, które mają taką samą nazwę jak Klasa.

Poniższy przykład generuje C2523:

```cpp
// C2523.cpp
// compile with: /c
class A {
   ~B();    // C2523
   ~A();   // OK
};
```

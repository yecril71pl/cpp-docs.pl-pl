---
title: C2255 błąd kompilatora
ms.date: 11/04/2016
f1_keywords:
- C2255
helpviewer_keywords:
- C2255
ms.assetid: 67dc4cb0-de6b-4405-bd64-d47736367a93
ms.openlocfilehash: ae2c61257af3e1aca2d26ce5f8801999f7bb77c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429396"
---
# <a name="compiler-error-c2255"></a>C2255 błąd kompilatora

"element": niedozwolone poza definicją klasy

Na przykład funkcja niebędących jest zadeklarowana `friend`.

Poniższy przykład spowoduje wygenerowanie C2255:

```
// C2255.cpp
// compile with: /c
class A {
private:
   void func1();
   friend void func2();
};

friend void func1() {}   // C2255
void func2(){}
```
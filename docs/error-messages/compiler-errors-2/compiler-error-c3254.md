---
title: Błąd kompilatora C3254
ms.date: 11/04/2016
f1_keywords:
- C3254
helpviewer_keywords:
- C3254
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
ms.openlocfilehash: 7e051c6c44d3b85f6f3faaf5380ecf54cba5d73c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470671"
---
# <a name="compiler-error-c3254"></a>Błąd kompilatora C3254

"jawnego przesłaniania": klasa zawiera jawne przesłonięcie "override", ale nie pochodzi z interfejsu, który zawiera deklarację funkcji

Gdy użytkownik [jawnie przesłonić](../../cpp/explicit-overrides-cpp.md) metody, klasy, która zawiera przesłonięcie muszą pochodzić, bezpośrednio lub pośrednio, z typu, który zawiera funkcję zastępowania.

Poniższy przykład spowoduje wygenerowanie C3254:

```
// C3254.cpp
__interface I
{
   void f();
};

__interface I1 : I
{
};

struct A /* : I1 */
{
   void I1::f()
   {   // C3254, uncomment : I1 to resolve this C3254
   }
};

int main()
{
}
```
---
title: Błąd kompilatora C3254
ms.date: 11/04/2016
f1_keywords:
- C3254
helpviewer_keywords:
- C3254
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
ms.openlocfilehash: 6b9ff41fb4f45d9570869ca90e3c6091cc03a58a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754254"
---
# <a name="compiler-error-c3254"></a>Błąd kompilatora C3254

"jawne przesłonięcie": Klasa zawiera jawne przesłonięcie "override", ale nie pochodzi z interfejsu, który zawiera deklarację funkcji

W przypadku [jawnego przesłaniania](../../cpp/explicit-overrides-cpp.md) metody Klasa, która zawiera przesłonięcie, musi pochodzić, bezpośrednio lub pośrednio, z typu, który zawiera zastępujący funkcję.

Poniższy przykład generuje C3254:

```cpp
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

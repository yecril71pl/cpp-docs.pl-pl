---
title: Błąd kompilatora C3611
ms.date: 11/04/2016
f1_keywords:
- C3611
helpviewer_keywords:
- C3611
ms.assetid: 42f3e320-41de-420a-bd05-8924cab765aa
ms.openlocfilehash: 1fedcf406e101c87c5c831ef1b6d82fea0bbfa02
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755931"
---
# <a name="compiler-error-c3611"></a>Błąd kompilatora C3611

"Function": funkcja zapieczętowana nie może mieć czystego specyfikatora

Funkcja zapieczętowana została zadeklarowana nieprawidłowo.  Aby uzyskać więcej informacji, zobacz [zapieczętowany](../../extensions/sealed-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3611.

```cpp
// C3611.cpp
// compile with: /clr /c

ref struct V {
   virtual void Test() sealed = 0;   // C3611
   virtual void Test2() sealed;   // OK
   virtual void Test3() = 0;   // OK
};
```

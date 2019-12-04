---
title: Błąd kompilatora C3662
ms.date: 11/04/2016
f1_keywords:
- C3662
helpviewer_keywords:
- C3662
ms.assetid: 61bd3e41-a86b-42c0-be89-d992d3906ff1
ms.openlocfilehash: 48fe8bd4a6872ff214d185ac77553debab78ab20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758193"
---
# <a name="compiler-error-c3662"></a>Błąd kompilatora C3662

"member": specyfikator przesłonięcia "Only" jest dozwolony tylko dla funkcji składowych klas zarządzanych lub WinRT

Użyto specyfikatora przesłonięcia dla elementu członkowskiego typu natywnego, co jest niedozwolone.

Aby uzyskać więcej informacji, zobacz [jawne zastąpienia](../../extensions/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3662.

```cpp
// C3662.cpp
// compile with: /clr /c
struct S {
   virtual void f();
};

struct S1 : S {
   virtual void f() new;   // C3662
};

ref struct T {
   virtual void f();
};

ref struct T1 : T {
   virtual void f() new;   // OK
};
```

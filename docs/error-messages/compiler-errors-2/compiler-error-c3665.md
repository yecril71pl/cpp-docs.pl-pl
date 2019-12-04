---
title: Błąd kompilatora C3665
ms.date: 11/04/2016
f1_keywords:
- C3665
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
ms.openlocfilehash: 4b0c019b2425b314f5b3503db41042d917283aa8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758180"
---
# <a name="compiler-error-c3665"></a>Błąd kompilatora C3665

"destruktor": specyfikator przesłonięcia "słowo kluczowe" jest niedozwolony w destruktorze/finalizatorze

Użyto słowa kluczowego, które jest niedozwolone w destruktorze lub finalizatorze.

Na przykład nie można zażądać nowego miejsca na destruktorze lub finalizatorze.  Aby uzyskać więcej informacji, zobacz [jawne zastąpienia](../../extensions/explicit-overrides-cpp-component-extensions.md) i [destruktory oraz finalizatory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Poniższy przykład generuje C3665:

```cpp
// C3665.cpp
// compile with: /clr
public ref struct R {
   virtual ~R() { }
   virtual void a() { }
};

public ref struct S : R {
   virtual ~S() new {}   // C3665
   virtual void a() new {}   // OK
};
```

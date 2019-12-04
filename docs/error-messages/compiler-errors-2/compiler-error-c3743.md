---
title: Błąd kompilatora C3743
ms.date: 11/04/2016
f1_keywords:
- C3743
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
ms.openlocfilehash: c0e2082dc87c6236aa11dd3094d056b0024dfc2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752473"
---
# <a name="compiler-error-c3743"></a>Błąd kompilatora C3743

można tylko podpiąć/odpiąć cały interfejs, gdy parametr "layout_dependent" event_receiver ma wartość true

Funkcja [__unhook](../../cpp/unhook.md) różni się w zależności od liczby parametrów pobieranych na podstawie wartości przesłanej do parametru `layout_dependent` w klasie [event_receiver](../../windows/event-receiver.md) .

Poniższy przykład generuje C3743:

```cpp
// C3743.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];
[object] __interface I { HRESULT f(); };

[event_receiver(com, layout_dependent=true), coclass]
struct R : I {
        HRESULT f() {
      return 0;
   }
        R() {
   }

   R(I* a) {
      __hook(I, a, &R::f);   // C3743
      // The following line resolves the error.
      // __hook(I, a);
   }
};
```

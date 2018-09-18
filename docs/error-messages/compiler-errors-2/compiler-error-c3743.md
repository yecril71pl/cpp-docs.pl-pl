---
title: Błąd kompilatora C3743 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3743
dev_langs:
- C++
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99988a9a0fb3afb197e081c45f6f5446d55b801c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019072"
---
# <a name="compiler-error-c3743"></a>Błąd kompilatora C3743

można tylko zaczepić/odczepić cały interfejs podczas parametr "layout_dependent" od event_receiver ma wartość true

[__Unhook](../../cpp/unhook.md) funkcja różni się w liczbie parametrów, które przyjmuje oparte na wartości przekazane do `layout_dependent` parametru w [event_receiver](../../windows/event-receiver.md) klasy.

Poniższy przykład spowoduje wygenerowanie C3743:

```
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
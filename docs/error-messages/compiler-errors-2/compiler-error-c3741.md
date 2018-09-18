---
title: Błąd kompilatora C3741 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3741
dev_langs:
- C++
helpviewer_keywords:
- C3741
ms.assetid: ed311315-cc32-49c9-97fa-01b293d81526
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 531b2765bb829a6278bf2d1ca663733f6279b1b4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106900"
---
# <a name="compiler-error-c3741"></a>Błąd kompilatora C3741

"class": musi być klasą coclass gdy parametr "layout_dependent" od event_receiver = true

Gdy `layout_dependent=true` dla [event_receiver](../../windows/event-receiver.md) klasy, a następnie klasy musi mieć również [coclass](../../windows/coclass.md) atrybutu.

Poniższy przykład spowoduje wygenerowanie C3741

```
// C3741.cpp
// compile with: /c
// C3741 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I{ HRESULT f(); };

// Delete the following line to resolve.
[ event_receiver(com, layout_dependent=true)]

// class or struct must be declared with coclass
// Uncomment the following line to resolve.
// [ event_receiver(com, layout_dependent=true), coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct R : I {
   HRESULT f(){ return 0; }
   R(){}
   R(I* a){ __hook(I, a); }
};
```
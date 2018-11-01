---
title: Błąd kompilatora C3719
ms.date: 11/04/2016
f1_keywords:
- C3719
helpviewer_keywords:
- C3719
ms.assetid: d0d59d4e-babb-4480-9ef7-70cf1a28165c
ms.openlocfilehash: 3ead2f18cdc8b76a0bb3da30e7086bdc80b49d43
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471933"
---
# <a name="compiler-error-c3719"></a>Błąd kompilatora C3719

"interface": źródło zdarzeń bazujące na interfejsie należy używać tylko dla zdarzeń COM

Interfejs w kontekście COM nie została zadeklarowana.

Poniższy przykład spowoduje wygenerowanie C3719:

```
// C3719a.cpp
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];

[object]
__interface I {
   HRESULT func1();
};

[event_source(native), coclass]
struct A {
   __event __interface I;   // C3719

   // try the following line instead
   // __event func2();
};

int main() {
}
```

Aby naprawić ten błąd, należy zastosować [obiektu](../../windows/object-cpp.md), [coclass](../../windows/coclass.md), [event_source](../../windows/event-source.md), i [event_receiver](../../windows/event-receiver.md) atrybuty odpowiednio się klasy, w których korzysta z klas interfejsu COM. Na przykład:

```
// C3719b.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[module(name="xx")];
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f();
};

[coclass, event_source(com) , uuid("00000000-0000-0000-0000-000000000002")]
struct MyStruct {
   __event __interface I;
};

[event_receiver(com)]
struct MyStruct2 {
   void f() {
   }
   MyStruct2(I* pB) {
      __hook(&I::f, pB, &MyStruct2::f);
   }
};

int main()
{
}
```
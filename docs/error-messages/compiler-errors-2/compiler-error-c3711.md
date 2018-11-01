---
title: Błąd kompilatora C3711
ms.date: 11/04/2016
f1_keywords:
- C3711
helpviewer_keywords:
- C3711
ms.assetid: 26d581cc-2153-4ee0-b814-a371184be3e1
ms.openlocfilehash: 391b78077ea526ebbaf99552b3220f85928a9096
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508813"
---
# <a name="compiler-error-c3711"></a>Błąd kompilatora C3711

"method": metoda źródłowej niezarządzanej zdarzeń musi zwrócić void lub typ całkowity

Metoda jest zdefiniowana w źródło zdarzenia, który nie został zwrócony typ void lub typ całkowity. Aby naprawić ten błąd, upewnij się zdarzenia, a program obsługi zdarzeń, które mają zwracany typ `void` lub typem całkowitym, takie jak `int` lub `long`.

Poniższy przykład spowoduje wygenerowanie C3711:

```
// C3711.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[event_source(native)]
class CEventSrc {
public:
   __event float event1();   // C3711
   // try the following line instead
   // __event int event1();
   // also change the handler, below
};

[event_receiver(native)]
class CEventRec {
public:
   float handler1() {         // change float to int
      return 0.0;             // change 0.0 to 0
   }
   void HookEvents(CEventSrc* pSrc) {
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }
   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};

int main() {
}
```
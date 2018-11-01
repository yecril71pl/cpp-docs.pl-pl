---
title: Błąd kompilatora C3703
ms.date: 11/04/2016
f1_keywords:
- C3703
helpviewer_keywords:
- C3703
ms.assetid: 7e3677d9-f2be-4c26-998f-423564e9023c
ms.openlocfilehash: 0b34760bc3f5b23148ce84cf590685efad2008df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428083"
---
# <a name="compiler-error-c3703"></a>Błąd kompilatora C3703

"program obsługi zdarzeń": metoda obsługi zdarzeń musi mieć tą samą klasę magazynu jako źródła "event"

[Zdarzeń](../../cpp/event-handling.md) ma klasę magazynu innego niż program obsługi zdarzeń, do którego jest podłączone. Na przykład ten błąd występuje, jeśli procedura obsługi zdarzeń jest statyczną funkcją składową, a zdarzenie nie jest statyczne. Aby naprawić ten błąd, zapewniają zdarzenia i tą samą klasę magazynu programu obsługi zdarzeń.

Poniższy przykład spowoduje wygenerowanie C3703:

```
// C3703.cpp
// C3703 expected
#include <stdio.h>

[event_source(type=native)]
class CEventSrc {
public:
   __event static void MyEvent();
};

[event_receiver(type=native)]
class CEventHandler {
public:
   // delete the following line to resolve
   void MyHandler() {}

   // try the following line instead
   // static void MyHandler() {}

   void HookIt(CEventSrc* pSource) {
      __hook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);
   }

   void UnhookIt(CEventSrc* pSource) {
      __unhook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);
   }
};

int main() {
   CEventSrc src;
   CEventHandler hnd;

   hnd.HookIt(&src);
   __raise src.MyEvent();
   hnd.UnhookIt(&src);
}
```
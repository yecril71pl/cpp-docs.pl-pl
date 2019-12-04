---
title: Błąd kompilatora C3703
ms.date: 11/04/2016
f1_keywords:
- C3703
helpviewer_keywords:
- C3703
ms.assetid: 7e3677d9-f2be-4c26-998f-423564e9023c
ms.openlocfilehash: 1071623c8dbaef52a6a391d8858e7502de9c74b4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757998"
---
# <a name="compiler-error-c3703"></a>Błąd kompilatora C3703

"Obsługa zdarzeń": metoda obsługi zdarzeń musi mieć tę samą klasę magazynu co Źródło "Event"

[Zdarzenie](../../cpp/event-handling.md) ma inną klasę magazynu niż program obsługi zdarzeń, do którego jest podłączany. Na przykład ten błąd występuje, jeśli program obsługi zdarzeń jest statyczną funkcją składową, a zdarzenie nie jest statyczne. Aby naprawić ten błąd, nadaj zdarzeniu i obsłudze zdarzeń tę samą klasę magazynu.

Poniższy przykład generuje C3703:

```cpp
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

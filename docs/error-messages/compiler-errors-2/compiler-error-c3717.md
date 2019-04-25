---
title: Błąd kompilatora C3717
ms.date: 11/04/2016
f1_keywords:
- C3717
helpviewer_keywords:
- C3717
ms.assetid: ae4fceb1-2583-4577-b2f1-40971a017055
ms.openlocfilehash: f7e60b4f1b6a1337ef93088e4f36ce2a1b34dc47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328279"
---
# <a name="compiler-error-c3717"></a>Błąd kompilatora C3717

"method": metoda wyzwalająca zdarzenia nie może być zdefiniowana

Możesz zadeklarować metodę zdarzeń, który zawiera implementację. [__Event](../../cpp/event.md) deklaracji metody nie może mieć definicji. Aby naprawić ten błąd, zapewnić nie deklaracje metody zdarzeń definicje. Na przykład w poniższym kodzie usunąć treści funkcji z `event1` deklaracji, wskazane przez komentarze.

Poniższy przykład spowoduje wygenerowanie C3717:

```
// C3717.cpp
[event_source(native)]
class CEventSrc {
public:
   __event void event1() {   // C3717
   }

   // remove definition for event1 and substitute following declaration
   // __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {
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
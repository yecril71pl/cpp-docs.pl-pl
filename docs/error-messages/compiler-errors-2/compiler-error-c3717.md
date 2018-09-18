---
title: Błąd kompilatora C3717 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3717
dev_langs:
- C++
helpviewer_keywords:
- C3717
ms.assetid: ae4fceb1-2583-4577-b2f1-40971a017055
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75c770ecfc914c033c1db71578cda137d632e363
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086700"
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
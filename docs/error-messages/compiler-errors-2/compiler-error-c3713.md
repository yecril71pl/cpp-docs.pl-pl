---
title: Błąd kompilatora C3713
ms.date: 11/04/2016
f1_keywords:
- C3713
helpviewer_keywords:
- C3713
ms.assetid: 75c6b9b6-955b-49bd-9bc8-ced88b496a1f
ms.openlocfilehash: 8c8c3b5e6016c7f4af471a163463c91d478fea91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444567"
---
# <a name="compiler-error-c3713"></a>Błąd kompilatora C3713

"method": metoda obsługi zdarzeń musi mieć te same parametry funkcji jako źródło "method"

Zdefiniowane metody obsługi zdarzeń, które nie było używane te same parametry jako metoda źródła zdarzeń. Aby naprawić ten błąd, należy podać metodę programu obsługi zdarzeń te same parametry, jak te metody źródła zdarzeń.

Poniższy przykład spowoduje wygenerowanie C3713:

```
// C3713.cpp
// compile with: /c
[event_source(native)]
class CEventSrc {
public:
   __event void event1(int nValue);
   // try the following line instead
   // __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3713
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3713
   }
};
```
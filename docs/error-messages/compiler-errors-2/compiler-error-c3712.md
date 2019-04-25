---
title: Błąd kompilatora C3712
ms.date: 11/04/2016
f1_keywords:
- C3712
helpviewer_keywords:
- C3712
ms.assetid: 65b1fcaf-be89-4c55-9e40-25ec03457253
ms.openlocfilehash: 0b84f4562dcc0dd5dcc3ecb647316772efab6b38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328409"
---
# <a name="compiler-error-c3712"></a>Błąd kompilatora C3712

"method": metoda obsługi zdarzeń musi zwracać taki sam typ jak źródło "method"

Zdefiniowane metody obsługi zdarzeń, która nie zwróciła tego samego typu co metoda źródła zdarzeń. Aby naprawić ten błąd, należy podać metodę programu obsługi zdarzeń taki sam zwracany typ jak metoda źródła zdarzeń.

Poniższy przykład spowoduje wygenerowanie C3712:

```
// C3712.cpp
// compile with: /c
[event_source(native)]
class CEventSrc {
public:
   __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   int handler1() { return 0; }
   // try the following line instead
   // void handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3712
   }
   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3712
   }
};
```
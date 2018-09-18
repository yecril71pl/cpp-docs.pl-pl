---
title: Błąd kompilatora C3713 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3713
dev_langs:
- C++
helpviewer_keywords:
- C3713
ms.assetid: 75c6b9b6-955b-49bd-9bc8-ced88b496a1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8028a82895d9194a44ca844b628e6a0d96ef4811
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042627"
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
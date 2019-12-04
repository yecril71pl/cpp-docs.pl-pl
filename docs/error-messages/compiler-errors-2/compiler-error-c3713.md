---
title: Błąd kompilatora C3713
ms.date: 11/04/2016
f1_keywords:
- C3713
helpviewer_keywords:
- C3713
ms.assetid: 75c6b9b6-955b-49bd-9bc8-ced88b496a1f
ms.openlocfilehash: d78d1fb3028e8618035c1c6f7bb3eb0f65409dd2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753357"
---
# <a name="compiler-error-c3713"></a>Błąd kompilatora C3713

"Metoda": metoda obsługi zdarzeń musi mieć te same parametry funkcji co Źródło "Metoda"

Zdefiniowano metodę procedury obsługi zdarzeń, która nie korzystała z tych samych parametrów co źródłowa Metoda zdarzenia. Aby naprawić ten błąd, nadaj metodzie obsługi zdarzeń te same parametry jak te, które są źródłowe metody zdarzenia.

Poniższy przykład generuje C3713:

```cpp
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

---
title: Błąd kompilatora C3709 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3709
dev_langs:
- C++
helpviewer_keywords:
- C3709
ms.assetid: d5576b04-2f93-420a-8f3e-8b8e987e8dab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e0e64a07257cf55df028383cd5347ad64eb702f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091728"
---
# <a name="compiler-error-c3709"></a>Błąd kompilatora C3709

'Funkcja': Niewłaściwa składnia określająca zdarzenie w __hook /\__unhook

Podczas określania źródła zdarzeń za pomocą [__hook](../../cpp/hook.md) lub [__unhook](../../cpp/unhook.md), pierwszy parametr musi być metodą ważnego zdarzenia i drugi parametr musi być obiektem źródłowym ważnego zdarzenia (nie metoda).

Poniższy przykład spowoduje wygenerowanie C3709:

```
// C3709.cpp
// compile with: /LD
[event_source(native)]
class CEventSrc
{
public:
   __event void event1();
};

[event_receiver(native)]
class CEventRec
{
public:
   void handler1()
   {
   }

   void HookEvents(CEventSrc* pSrc)
   {
      __hook(bad, pSrc, CEventRec::handler1);   // C3709
      // Try the following line instead:
      // __hook(&CEventSrc::event1, pSrc, CEventRec::handler1);
   }

   void UnhookEvents(CEventSrc* pSrc)
   {
      __unhook(&CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};
```
---
title: Błąd kompilatora C3703 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3703
dev_langs:
- C++
helpviewer_keywords:
- C3703
ms.assetid: 7e3677d9-f2be-4c26-998f-423564e9023c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 730409d9db313294e23693b6d50d4b0aff0f8869
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043888"
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
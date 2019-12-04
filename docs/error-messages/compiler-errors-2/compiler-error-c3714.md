---
title: Błąd kompilatora C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: 1078bf8a97f6cb7afeaf7046489fe262c0bb0199
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753331"
---
# <a name="compiler-error-c3714"></a>Błąd kompilatora C3714

"Metoda": metoda obsługi zdarzeń musi mieć taką samą konwencję wywołania jak Źródło "Metoda"

Zdefiniowano metodę procedury obsługi zdarzeń, która nie korzystała z tej samej konwencji wywoływania co źródłowa Metoda zdarzenia. Aby naprawić ten błąd, nadaj metodzie obsługi zdarzeń te same konwencje wywoływania, jak te w źródłowej metodzie zdarzenia. Na przykład, w poniższym kodzie, ustaw konwencje wywoływania `handler1` i `event1` dopasowanie ([__cdecl](../../cpp/cdecl.md) lub [__stdcall](../../cpp/stdcall.md) lub innych). Usunięcie słów kluczowych konwencji wywoływania z obu deklaracji spowoduje również rozwiązanie problemu i spowoduje, że `event1` i `handler1` domyślnie do konwencji wywoływania [thiscall](../../cpp/thiscall.md) . Aby uzyskać więcej informacji, zobacz [konwencje wywoływania](../../cpp/calling-conventions.md) .

Poniższy przykład generuje C3714:

```cpp
// C3714.cpp
// compile with: /c
// processor: x86
[event_source(native)]
class CEventSrc {
public:
   __event void __cdecl event1();
   // try the following line instead
   // __event void __stdcall event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void __stdcall handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3714
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3714
   }
};
```

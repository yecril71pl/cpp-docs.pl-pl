---
title: C3714 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3714
dev_langs:
- C++
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0046463b7354d0b764e29701bddb117496858e14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3714"></a>C3714 błąd kompilatora
"metoda": metoda obsługi zdarzeń musi mieć tą samą konwencję wywołania jako źródło "method"  
  
 Definicja jest metoda obsługi zdarzeń, który nie używa tej samej Konwencji wywołania metodą źródła zdarzeń. Aby naprawić ten błąd, należy podać metoda obsługi zdarzeń tej samej konwencji wywoływania jak metoda zdarzeń źródła. Na przykład w poniższym kodzie należy konwencji wywoływania programu `handler1` i `event1` zgodne ([__cdecl](../../cpp/cdecl.md) lub [__stdcall](../../cpp/stdcall.md) lub innych). Usuwanie wywoływanie Konwencji słów kluczowych z obu deklaracjach będzie również umożliwić rozwiązanie tego problemu i spowodować `event1` i `handler1` domyślnie [thiscall](../../cpp/thiscall.md) konwencji wywoływania. Zobacz [konwencji wywoływania](../../cpp/calling-conventions.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C3714:  
  
```  
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
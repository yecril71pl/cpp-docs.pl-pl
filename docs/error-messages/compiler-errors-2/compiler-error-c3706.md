---
title: "C3706 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3706
dev_langs:
- C++
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b33ea3c7de9afc605622cc55f4a45f73350d7db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3706"></a>C3706 błąd kompilatora
"Funkcja": musi być interfejsem COM żeby wyzwalać zdarzenia COM  
  
 Interfejsu zdarzenia, który umożliwia wyzwalać zdarzenia COM musi być interfejsem COM. W takiej sytuacji interfejsu albo powinien być zdefiniowany za pomocą atrybutu Visual C++ lub zaimportowany za pomocą [#import](../../preprocessor/hash-import-directive-cpp.md) z atrybutem embedded_idl w #import biblioteki typów.  
  
 Należy pamiętać, że `#include` wierszy pliki nagłówkowe ATL pokazano w poniższym przykładzie są wymagane do używania zdarzeń COM. Aby naprawić ten błąd, należy `IEvents` (interfejsu zdarzeń) interfejsu COM, stosując jedną z następujących atrybutów do definicji interfejsu: [obiektu](../../windows/object-cpp.md), [podwójną](../../windows/dual.md), lub [ dispinterface](../../windows/dispinterface.md).  
  
 W przypadku interfejsu z pliku nagłówka wygenerowano przez MIDL, kompilator nie rozpoznaje ją jako interfejs COM.  
  
 Poniższy przykład generuje C3706:  
  
```  
// C3706.cpp  
// compile with: /c  
// C3706 expected  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];  
  
// Uncomment the following line to resolve.  
// [object, uuid="12341234-1234-1234-1234-123412341237"]  
__interface IEvents : IUnknown {  
   HRESULT event1(/*[in]*/ int i);   // uncomment [in]  
};  
  
[dual, uuid="12341234-1234-1234-1234-123412341235"]  
__interface IBase {  
   HRESULT fireEvents();  
};  
  
[coclass, event_source(com), uuid="12341234-1234-1234-1234-123412341236"]  
class CEventSrc : public IBase {  
   public:  
   __event __interface IEvents;  
  
   HRESULT fireEvents() {  
      HRESULT hr = IEvents_event1(123);  
      return hr;  
   }  
};  
```
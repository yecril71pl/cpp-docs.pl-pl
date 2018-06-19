---
title: C3706 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3706
dev_langs:
- C++
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8cb54dfce6a6974fcf09886f2d13047cdab53ced
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265249"
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
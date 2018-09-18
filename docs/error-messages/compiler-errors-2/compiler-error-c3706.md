---
title: Błąd kompilatora C3706 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: bbebf5752a9ed42ea4af8d3a13e45c78fc1753ec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110513"
---
# <a name="compiler-error-c3706"></a>Błąd kompilatora C3706

'Funkcja': musi być interfejsem COM żeby wyzwalać zdarzenia COM

Interfejs zdarzeń, którego używasz do wyzwalać zdarzenia COM musi być interfejsem COM. W takiej sytuacji interfejsu albo powinna być zdefiniowana za pomocą atrybutu Visual C++ lub importowane przy użyciu [#import](../../preprocessor/hash-import-directive-cpp.md) z biblioteki typów, przy użyciu atrybutu embedded_idl #import firmy.

Należy pamiętać, że `#include` wierszy plików nagłówkowych ATL. pokazano w poniższym przykładzie są wymagane do używania zdarzenia COM. Aby naprawić ten błąd, należy `IEvents` (interfejsu obsługi zdarzeń) interfejsu COM, stosując jedną z następujących atrybutów do definicji interfejsu: [obiektu](../../windows/object-cpp.md), [podwójną](../../windows/dual.md), lub [ dispinterface](../../windows/dispinterface.md).

Jeśli interfejs pochodzą z pliku nagłówka wygenerowano przez MIDL, kompilator nie rozpoznaje je jako interfejs COM.

Poniższy przykład spowoduje wygenerowanie C3706:

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
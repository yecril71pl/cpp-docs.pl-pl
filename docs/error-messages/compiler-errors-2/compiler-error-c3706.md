---
title: Błąd kompilatora C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: 2d474db5a4d50aed7b59e6f48fb5a3e8165f10c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468626"
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
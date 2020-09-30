---
title: Błąd kompilatora C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: 461850b2c1686343f23c77274b8fb2ca6fd9071e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508000"
---
# <a name="compiler-error-c3706"></a>Błąd kompilatora C3706

"Function": musi być interfejsem COM, aby uruchamiać zdarzenia COM

Interfejs zdarzenia używany do wyzwalania zdarzeń COM musi być interfejsem COM. W takiej sytuacji interfejs powinien być zdefiniowany przy użyciu atrybutu Visual C++ lub zaimportowany przy użyciu [#import](../../preprocessor/hash-import-directive-cpp.md) z biblioteki typów z atrybutem embedded_idl #import.

Należy zauważyć, że `#include` wiersze plików nagłówkowych ATL przedstawione w poniższym przykładzie są wymagane do korzystania z zdarzeń com. Aby naprawić ten błąd, wprowadź `IEvents` (interfejs zdarzenia) Interfejs com, stosując jeden z następujących atrybutów do definicji interfejsu: [Object](../../windows/attributes/object-cpp.md), [Dual](../../windows/attributes/dual.md)lub [dispinterface](../../windows/attributes/dispinterface.md).

Jeśli interfejs pochodzi z pliku nagłówka wygenerowanego przez MIDL, kompilator nie rozpoznaje go jako interfejsu COM.

Poniższy przykład generuje C3706:

```cpp
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

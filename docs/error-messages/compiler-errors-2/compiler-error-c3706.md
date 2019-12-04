---
title: Błąd kompilatora C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: 810ec59a814b04349913648fb49a03eb63912cd9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757985"
---
# <a name="compiler-error-c3706"></a>Błąd kompilatora C3706

"Function": musi być interfejsem COM, aby uruchamiać zdarzenia COM

Interfejs zdarzenia używany do wyzwalania zdarzeń COM musi być interfejsem COM. W takiej sytuacji interfejs powinien być zdefiniowany przy użyciu atrybutu wizualizacji C++ lub importowany przy użyciu [#import](../../preprocessor/hash-import-directive-cpp.md) z biblioteki typów z atrybutem embedded_idl #import.

Należy pamiętać, że w przypadku korzystania z zdarzeń COM wymagane są `#include` wierszy plików nagłówkowych ATL przedstawionych w poniższym przykładzie. Aby naprawić ten błąd, należy wprowadzić `IEvents` (interfejs zdarzenia) interfejsu COM, stosując jeden z następujących atrybutów do definicji interfejsu: [Object](../../windows/object-cpp.md), [Dual](../../windows/dual.md)lub [dispinterface](../../windows/dispinterface.md).

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

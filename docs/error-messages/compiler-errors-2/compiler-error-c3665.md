---
title: Błąd kompilatora C3665
ms.date: 11/04/2016
f1_keywords:
- C3665
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
ms.openlocfilehash: 40de7a7b1ede5e6dbbc20d2128b782c0ad6f798b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781032"
---
# <a name="compiler-error-c3665"></a>Błąd kompilatora C3665

"destruktor": specyfikator "— słowo kluczowe" nie jest dozwolone na destruktora/finalizatorze override

Słowo kluczowe użyto nie jest dozwolona na destruktora ani finalizatora.

Na przykład nowe miejsce nie można żądać na destruktora ani finalizatora.  Aby uzyskać więcej informacji, zobacz [jawne zastępowanie](../../extensions/explicit-overrides-cpp-component-extensions.md) i [destruktory i finalizatory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Poniższy przykład spowoduje wygenerowanie C3665:

```
// C3665.cpp
// compile with: /clr
public ref struct R {
   virtual ~R() { }
   virtual void a() { }
};

public ref struct S : R {
   virtual ~S() new {}   // C3665
   virtual void a() new {}   // OK
};
```
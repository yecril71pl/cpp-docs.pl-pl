---
title: Błąd kompilatora C3670
ms.date: 11/04/2016
f1_keywords:
- C3670
helpviewer_keywords:
- C3670
ms.assetid: d0fa9c6e-8f90-48c7-9066-31b4fa5942eb
ms.openlocfilehash: a9fe72501152891d3f82567f09922dda9a9b711a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775481"
---
# <a name="compiler-error-c3670"></a>Błąd kompilatora C3670

"override": nie można przesłonić metody niedostępnej klasy bazowej "method"

Zastąpienie może występować tylko w funkcji, których poziom dostępu udostępnia w typie pochodnym. Aby uzyskać więcej informacji, zobacz [jawne zastępowanie](../../extensions/explicit-overrides-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C3670:

```
// C3670.cpp
// compile with: /clr /c
public ref class C {
// Uncomment the following line to resolve.
// public:
   virtual void g() { }
};

public ref class D : public C {
public:
   virtual void f() new sealed = C::g {};   // C3670
};
```
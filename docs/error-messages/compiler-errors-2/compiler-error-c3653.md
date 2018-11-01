---
title: Błąd kompilatora C3653
ms.date: 11/04/2016
f1_keywords:
- C3653
helpviewer_keywords:
- C3653
ms.assetid: 316549d7-f7ef-4578-a2ba-57adc8aac527
ms.openlocfilehash: d7936303dab4fbb273a01f98def5b9af99f89dac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477626"
---
# <a name="compiler-error-c3653"></a>Błąd kompilatora C3653

'Funkcja': nie można użyć jako nazwanego przesłaniania: przesłaniana funkcja nie znaleziono; użytkownik zapomniał nadaj funkcji nazwę jawnie, przy użyciu:: operator?

Jawne przesłanianie określona funkcja, która nie została odnaleziona w dowolnym interfejsie. Aby uzyskać więcej informacji, zobacz [jawne zastępowanie](../../windows/explicit-overrides-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C3653:

```
// C3653.cpp
// compile with: /clr
public interface struct I {
   void h();
};

public ref struct X : public I {
   virtual void f() new sealed = J {};   // C3653 no J in scope
   virtual void g() {}   // OK
   virtual void h() new sealed = I::h {};   // OK
};
```
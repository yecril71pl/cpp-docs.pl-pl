---
title: Błąd kompilatora C3653
ms.date: 11/04/2016
f1_keywords:
- C3653
helpviewer_keywords:
- C3653
ms.assetid: 316549d7-f7ef-4578-a2ba-57adc8aac527
ms.openlocfilehash: 75e2c061190b24019491db7a625ecafb5ac82b6b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776447"
---
# <a name="compiler-error-c3653"></a>Błąd kompilatora C3653

'Funkcja': nie można użyć jako nazwanego przesłaniania: przesłaniana funkcja nie znaleziono; użytkownik zapomniał nadaj funkcji nazwę jawnie, przy użyciu:: operator?

Jawne przesłanianie określona funkcja, która nie została odnaleziona w dowolnym interfejsie. Aby uzyskać więcej informacji, zobacz [jawne zastępowanie](../../extensions/explicit-overrides-cpp-component-extensions.md).

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
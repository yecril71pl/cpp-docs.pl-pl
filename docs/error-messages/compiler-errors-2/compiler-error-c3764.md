---
title: Błąd kompilatora C3764
ms.date: 11/04/2016
f1_keywords:
- C3764
helpviewer_keywords:
- C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
ms.openlocfilehash: 2570ee9abb148b919242de7786cd6fa91765286f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58773583"
---
# <a name="compiler-error-c3764"></a>Błąd kompilatora C3764

"override_function": nie można przesłonić metody klasy bazowej "base_class_function"

Kompilator wykrył przesłonięciem źle sformułowane. Na przykład funkcji klasy bazowej nie `virtual`. Aby uzyskać więcej informacji, zobacz [zastąpienia](../../extensions/override-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3764.

```
// C3764.cpp
// compile with: /clr /c
public ref struct A {
   void g(int);
   virtual void h(int);
};

public ref struct B : A {
   virtual void g(int) override {}   // C3764
   virtual void h(int) override {}   // OK
};
```

## <a name="example"></a>Przykład

C3764 może również wystąpić, gdy metoda klasy bazowej jest jawnie o nazwie przesłonięcia. Poniższy przykład spowoduje wygenerowanie C3764.

```
// C3764_b.cpp
// compile with: /clr /c
ref struct A {
   virtual void Test() {}
};

ref struct B : public A {
   virtual void Test() override {}
   virtual void Test2() = A::Test {}   // C3764
};
```
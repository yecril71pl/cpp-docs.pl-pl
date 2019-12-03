---
title: Ostrzeżenie kompilatora (poziom 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: 1583da44368225eabd8181be970f69f6582111e1
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2019
ms.locfileid: "74682981"
---
# <a name="compiler-warning-level-4-c4487"></a>Ostrzeżenie kompilatora (poziom 4) C4487

"derived_class_function": pasuje do dziedziczonej metody niewirtualnej "base_class_function", ale nie jest jawnie oznaczona modyfikatorem "New"

Funkcja w klasie pochodnej ma ten sam podpis co niewirtualna funkcja klasy bazowej. C4487 przypomina o tym, że funkcja klasy pochodnej nie przesłania funkcji klasy bazowej. Jawnie Oznacz funkcję klasy pochodnej jako `new`, aby rozwiązać to ostrzeżenie.

Aby uzyskać więcej informacji, zobacz [Nowość (nowe miejsce w tabeli tablic wirtualnych)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4487.

```cpp
// C4487.cpp
// compile with: /W4 /clr
using namespace System;
public ref struct B {
   void f() { Console::WriteLine("in B::f"); }
   void g() { Console::WriteLine("in B::g"); }
};

public ref struct D : B {
   void f() { Console::WriteLine("in D::f"); }   // C4487
   void g() new { Console::WriteLine("in D::g"); }   // OK
};

int main() {
   B ^ a = gcnew D;
   // will call base class functions
   a->f();
   a->g();
}
```
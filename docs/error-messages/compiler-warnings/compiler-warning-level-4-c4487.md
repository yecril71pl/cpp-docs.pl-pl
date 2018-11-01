---
title: Kompilator ostrzeżenie (poziom 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: 743069c0ed3103a2ed8d459def65083146b971e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497040"
---
# <a name="compiler-warning-level-4-c4487"></a>Kompilator ostrzeżenie (poziom 4) C4487

"derived_class_function": pasuje do dziedziczonej metody niewirtualnej "base_class_function", ale to nie jawnie oznaczona modyfikatorem "new"

Funkcja w klasie pochodnej ma taki sam podpis, jak funkcja-wirtualnej klasy bazowej. C4487 przypomina o tym, że funkcja klasy pochodnej nie zastępuje funkcji klasy bazowej. Wyraźnie oznaczyć funkcja klasy pochodnej jako `new` można rozpoznać tego ostrzeżenia.

Aby uzyskać więcej informacji, zobacz [new (nowe gniazdo w vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4487.

```
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
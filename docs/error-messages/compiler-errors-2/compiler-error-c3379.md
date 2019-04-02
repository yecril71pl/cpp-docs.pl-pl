---
title: Błąd kompilatora C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 5bf4e2e42b4534d47a2a7d3c9a838c404a99ba68
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769993"
---
# <a name="compiler-error-c3379"></a>Błąd kompilatora C3379

"class": zagnieżdżona klasa nie może mieć specyfikatora dostępu do zestawu jako części swojej deklaracji

W przypadku zastosowania do typu zarządzanego, takich jak klasy lub struktury, [publicznych](../../cpp/public-cpp.md) i [prywatnej](../../cpp/private-cpp.md) słowa kluczowe wskazuje, czy klasa będzie udostępniana przez metadane zestawu. `public` lub `private` nie można zastosować do klasy zagnieżdżonej, która odziedziczy dostęp do zestawu otaczającej klasy.

Gdy jest używane z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), `ref` i `value` słowa kluczowe wskazują, że klasa jest zarządzana (zobacz [klas i struktur](../../extensions/classes-and-structs-cpp-component-extensions.md)).

Poniższy przykład spowoduje wygenerowanie C3379:

```
// C3379a.cpp
// compile with: /clr
using namespace System;

public ref class A {
public:
   static int i = 9;

   public ref class BA {   // C3379
   // try the following line instead
   // ref class BA {
   public:
      static int ii = 8;
   };
};

int main() {

   A^ myA = gcnew A;
   Console::WriteLine(myA->i);

   A::BA^ myBA = gcnew A::BA;
   Console::WriteLine(myBA->ii);
}
```

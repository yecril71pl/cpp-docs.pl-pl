---
title: Błąd kompilatora C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 9d99214f3ad7e7db1edc215d94c98e9cf9ec4ca2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742902"
---
# <a name="compiler-error-c3379"></a>Błąd kompilatora C3379

"Class": zagnieżdżona Klasa nie może mieć specyfikatora dostępu do zestawu jako części swojej deklaracji

W przypadku zastosowania do typu zarządzanego, takiego jak Klasa lub struktura, słowa kluczowe [Public](../../cpp/public-cpp.md) i [Private](../../cpp/private-cpp.md) wskazują, czy Klasa zostanie udostępniona za pomocą metadanych zestawu. nie można zastosować `public` lub `private` do klasy zagnieżdżonej, która odziedziczy dostęp do zestawu klasy otaczającej.

W przypadku użycia z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md)słowa kluczowe `ref` i `value` wskazują, że Klasa jest zarządzana (zobacz [klasy i struktury](../../extensions/classes-and-structs-cpp-component-extensions.md)).

Poniższy przykład generuje C3379:

```cpp
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

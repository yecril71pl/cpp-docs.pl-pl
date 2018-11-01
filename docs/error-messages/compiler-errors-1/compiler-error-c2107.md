---
title: Błąd kompilatora C2107
ms.date: 11/04/2016
f1_keywords:
- C2107
helpviewer_keywords:
- C2107
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
ms.openlocfilehash: 2b388495c6ce31452bd3f8e8bfc6c26a6bfbdbe8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643030"
---
# <a name="compiler-error-c2107"></a>Błąd kompilatora C2107

Nieprawidłowy indeks, pośrednik niedozwolony

Indeks dolny jest stosowany do wyrażenie, które nie zostało oszacowane jako wskaźnik.

## <a name="example"></a>Przykład

C2107 może wystąpić, jeśli niepoprawnie `this` wskaźnik dostęp indeksatora domyślnego typu do typu wartości. Aby uzyskać więcej informacji, zobacz [semantyka wskaźnika](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).

Poniższy przykład spowoduje wygenerowanie C2107.

```
// C2107.cpp
// compile with: /clr
using namespace System;

value struct B {
   property String ^ default[String ^] {
      String ^ get(String ^ data) {
         return "abc";
      }
   }
   void Test() {
      Console::WriteLine("{0}", this["aa"]);   // C2107
      Console::WriteLine("{0}", this->default["aa"]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```
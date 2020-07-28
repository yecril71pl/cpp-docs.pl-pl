---
title: Błąd kompilatora C2107
ms.date: 11/04/2016
f1_keywords:
- C2107
helpviewer_keywords:
- C2107
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
ms.openlocfilehash: 1be2ebb82aca481df9efbbc4ccdd54466ae60a3f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214792"
---
# <a name="compiler-error-c2107"></a>Błąd kompilatora C2107

niedozwolony indeks, operator pośredni jest niedozwolony

Indeks dolny jest stosowany do wyrażenia, które nie jest szacowane do wskaźnika.

## <a name="example"></a>Przykład

C2107 może wystąpić w przypadku nieprawidłowego użycia **`this`** wskaźnika typu wartości w celu uzyskania dostępu do domyślnego indeksatora typu. Aby uzyskać więcej informacji, zobacz [semantyka tego wskaźnika](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).

Poniższy przykład generuje C2107.

```cpp
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

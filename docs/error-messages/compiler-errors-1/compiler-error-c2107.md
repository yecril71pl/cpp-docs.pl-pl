---
title: Błąd kompilatora C2107 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2107
dev_langs:
- C++
helpviewer_keywords:
- C2107
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df81df38758cfdd9b3f62d9e0d241f0bf8578746
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097913"
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
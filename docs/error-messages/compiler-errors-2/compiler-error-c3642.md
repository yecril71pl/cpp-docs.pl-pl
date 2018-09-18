---
title: Błąd kompilatora C3642 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3642
dev_langs:
- C++
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: febd6f1a9a3b4bac8bbee59cbf8c5bead93c3fb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047723"
---
# <a name="compiler-error-c3642"></a>Błąd kompilatora C3642

Parametr "Typ_wyniku/args": nie można wywołać funkcji w Konwencji wywołania __clrcall z natywnego kodu

Funkcja, która jest oznaczona za pomocą [__clrcall](../../cpp/clrcall.md) konwencji wywoływania, nie można wywoływać z kodu natywnego (niezarządzanego).

*Typ_wyniku/args* nazwę funkcji lub typ `__clrcall` próby wywołania funkcji.  Typ jest używany w przypadku wywoływania za pomocą wskaźnika funkcji.

Do wywołania funkcji zarządzanej z kontekstu natywnej, można dodać funkcji "otoki", który będzie wybierany `__clrcall` funkcji. Ewentualnie można wykorzystać mechanizm kierujące CLR; zobacz [porady: przeprowadzanie Marshalingu funkcja wskaźników przy użyciu PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C3642:

```
// C3642.cpp
// compile with: /clr
using namespace System;
struct S {
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall
      Console::WriteLine(s);
   }
   void Test2(char * s) {
      Test(gcnew String(s));
   }
};

#pragma unmanaged
int main() {
   S s;
   s.Test("abc");   // C3642
   s.Test2("abc");   // OK
}
```
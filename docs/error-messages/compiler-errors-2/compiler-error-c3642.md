---
title: Błąd kompilatora C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: d524c49075c400caa345dd26ed681734ea0cfb94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385624"
---
# <a name="compiler-error-c3642"></a>Błąd kompilatora C3642

Parametr "Typ_wyniku/args": nie można wywołać funkcji w Konwencji wywołania __clrcall z natywnego kodu

Funkcja, która jest oznaczona za pomocą [__clrcall](../../cpp/clrcall.md) konwencji wywoływania, nie można wywoływać z kodu natywnego (niezarządzanego).

*Typ_wyniku/args* nazwę funkcji lub typ `__clrcall` próby wywołania funkcji.  Typ jest używany w przypadku wywoływania za pomocą wskaźnika funkcji.

Do wywołania funkcji zarządzanej z kontekstu natywnej, można dodać funkcji "otoki", który będzie wybierany `__clrcall` funkcji. Ewentualnie można wykorzystać mechanizm kierujące CLR; zobacz [jak: Przeprowadzanie marshalingu wskaźników funkcji za pomocą funkcji PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) Aby uzyskać więcej informacji.

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
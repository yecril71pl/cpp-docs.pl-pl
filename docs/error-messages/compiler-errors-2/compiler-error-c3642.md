---
title: Błąd kompilatora C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: 7c3f9f05bf04c9a1c20fff7910836e7b50468a8e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742460"
---
# <a name="compiler-error-c3642"></a>Błąd kompilatora C3642

"return_type/args": nie można wywołać funkcji z konwencją wywoływania __clrcall z kodu natywnego

Funkcja oznaczona przy użyciu konwencji wywoływania [__clrcall](../../cpp/clrcall.md) nie może być wywoływana z kodu natywnego (niezarządzanego).

*return_type/args* jest nazwą funkcji lub typem funkcji `__clrcall`, którą próbujesz wywołać.  Typ jest używany, gdy jest wywoływany przez wskaźnik funkcji.

Aby wywołać funkcję zarządzaną z kontekstu natywnego, można dodać funkcję "otoki", która wywoła funkcję `__clrcall`. Można też użyć mechanizmu Marshaling środowiska CLR. Zobacz [jak: kierowanie wskaźników funkcji za pomocą PInvoke,](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) Aby uzyskać więcej informacji.

Poniższy przykład generuje C3642:

```cpp
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

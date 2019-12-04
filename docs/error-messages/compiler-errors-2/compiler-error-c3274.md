---
title: Błąd kompilatora C3274
ms.date: 11/04/2016
f1_keywords:
- C3274
helpviewer_keywords:
- C3274
ms.assetid: 1f03f18e-b569-48eb-9249-11c70122a305
ms.openlocfilehash: d28deea0729a091ce0829187323a0d5a2d184944
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753825"
---
# <a name="compiler-error-c3274"></a>Błąd kompilatora C3274

__finally/finally bez dopasowania try

Nie znaleziono instrukcji [__finally](../../cpp/try-finally-statement.md) lub [finally](../../dotnet/finally.md) bez pasującego `try`. Aby rozwiązać ten problem, Usuń instrukcję `__finally` lub Dodaj instrukcję `try` dla `__finally`.

Poniższy przykład generuje C3274:

```cpp
// C3274.cpp
// compile with: /clr
// C3274 expected
using namespace System;
int main() {
   try {
      try {
         throw gcnew ApplicationException();
      }
      catch(...) {
         Console::Error->WriteLine(L"Caught an exception");
      }
      finally {
         Console::WriteLine(L"In finally");
      }
   } finally {
      Console::WriteLine(L"In finally");
   }

   // Uncomment the following 3 lines to resolve.
   // try {
   //   throw gcnew ApplicationException();
   // }

   finally {
      Console::WriteLine(L"In finally");
   }
   Console::WriteLine(L"**FAIL**");
}
```

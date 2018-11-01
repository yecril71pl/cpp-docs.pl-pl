---
title: Błąd kompilatora C3842
ms.date: 11/04/2016
f1_keywords:
- C3842
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
ms.openlocfilehash: a61a69aca53f7f8996d0261a57b749930ecc01cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638350"
---
# <a name="compiler-error-c3842"></a>Błąd kompilatora C3842

'Funkcja': kwalifikatory "const" i "volatile" dla funkcji składowych WinRT lub typy zarządzane nie są obsługiwane.

[Const](../../cpp/const-cpp.md) i [volatile](../../cpp/volatile-cpp.md) nie są obsługiwane dla funkcji składowych Windows Runtime lub typami zarządzanymi.

Poniższy przykład spowoduje wygenerowanie C3842:

```
// C3842a.cpp
// compile with: /clr /c
public ref struct A {
   void f() const {}   // C3842
   void f() volatile {}   // C3842

   void f() {}
};
```
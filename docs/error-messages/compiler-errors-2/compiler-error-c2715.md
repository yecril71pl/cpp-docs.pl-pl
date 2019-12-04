---
title: Błąd kompilatora C2715
ms.date: 11/04/2016
f1_keywords:
- C2715
helpviewer_keywords:
- C2715
ms.assetid: c81567a7-5b65-468f-aaf9-835f91e468e4
ms.openlocfilehash: 24f972452f9c823d2082e1c29758b39f088021d0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760533"
---
# <a name="compiler-error-c2715"></a>Błąd kompilatora C2715

"Type": nie można zgłosić lub przechwycić tego typu

Typy wartości nie są prawidłowymi argumentami w przypadku korzystania z obsługi wyjątków w kodzie zarządzanym (zobacz [Obsługa wyjątków](../../extensions/exception-handling-cpp-component-extensions.md) , aby uzyskać więcej informacji).

```cpp
// C2715a.cpp
// compile with: /clr
using namespace System;

value struct V {
   int i;
};

void f1() {
   V v;
   v.i = 10;
   throw v;   // C2715
   // try the following line instead
   // throw ((V^)v);
}

int main() {
   try {
      f1();
   }

   catch(V v) { if ( v.i == 10 ) {   // C2715
   // try the following line instead
   // catch(V^ pv) { if ( pv->i == 10 ) {
         Console::WriteLine("caught 10 - looks OK");
      }
      else {
         Console::WriteLine("catch looks bad");
      }
   }
   catch(...) {
      Console::WriteLine("catch looks REALLY bad");
   }
}
```

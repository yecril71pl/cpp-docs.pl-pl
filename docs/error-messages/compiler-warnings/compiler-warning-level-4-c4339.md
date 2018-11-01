---
title: Kompilator ostrzeżenie (poziom 4) C4339
ms.date: 11/04/2016
f1_keywords:
- C4339
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
ms.openlocfilehash: bc9d335b3a09f7953a12b388d5bb40cc4d433969
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567768"
---
# <a name="compiler-warning-level-4-c4339"></a>Kompilator ostrzeżenie (poziom 4) C4339

"type": użycie niezdefiniowanego typu wykryte w WinRT, czy CLR meta-data - użycie tego typu może prowadzić do wyjątku czasu wykonywania

Typ nie został zdefiniowany w kodzie, który został skompilowany dla środowiska uruchomieniowego Windows lub środowisko uruchomieniowe języka wspólnego. Zdefiniuj typ, aby uniknąć wyjątek czasu wykonywania to możliwe.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład generuje C4339 i pokazuje, jak go naprawić:

```
// C4339.cpp
// compile with: /W4 /clr /c
// C4339 expected
#pragma warning(default : 4339)

// Delete the following line to resolve.
class A;

// Uncomment the following line to resolve.
// class A{};

class X {
public:
   X() {}

   virtual A *mf() {
      return 0;
   }
};

X * f() {
   return new X();
}
```
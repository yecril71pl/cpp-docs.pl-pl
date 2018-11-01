---
title: Błąd kompilatora C2452
ms.date: 11/04/2016
f1_keywords:
- C2452
helpviewer_keywords:
- C2452
ms.assetid: a4ec7642-6660-4c7a-9866-853d1cc67daf
ms.openlocfilehash: 9b9f2c41da1eb36aceece7f14ad5c33b38404bb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523707"
---
# <a name="compiler-error-c2452"></a>Błąd kompilatora C2452

"type": nieprawidłowy typ źródłowy dla safe_cast

Typem źródła dla [safe_cast](../../windows/safe-cast-cpp-component-extensions.md) był nieprawidłowy.  Na przykład, wszystkie typy w `safe_cast` operacji musi być typu CLR.

Poniższy przykład spowoduje wygenerowanie C2452:

```
// C2452.cpp
// compile with: /clr

struct A {};
struct B : public A {};

ref struct C {};
ref struct D : public C{};

int main() {
   A a;
   safe_cast<B*>(&a);   // C2452

   // OK
   C ^ c = gcnew C;
   safe_cast<D^>(c);
}
```
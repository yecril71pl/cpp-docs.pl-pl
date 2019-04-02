---
title: Błąd kompilatora C2452
ms.date: 11/04/2016
f1_keywords:
- C2452
helpviewer_keywords:
- C2452
ms.assetid: a4ec7642-6660-4c7a-9866-853d1cc67daf
ms.openlocfilehash: 3e2d583efa2b634cf49d8588fa398bd81f24c607
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781110"
---
# <a name="compiler-error-c2452"></a>Błąd kompilatora C2452

"type": nieprawidłowy typ źródłowy dla safe_cast

Typem źródła dla [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) był nieprawidłowy.  Na przykład, wszystkie typy w `safe_cast` operacji musi być typu CLR.

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
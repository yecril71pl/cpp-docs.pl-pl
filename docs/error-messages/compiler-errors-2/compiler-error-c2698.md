---
title: Błąd kompilatora C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: f643b7d8c035b4d1d7d8806feb5b121cf76d7796
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651915"
---
# <a name="compiler-error-c2698"></a>Błąd kompilatora C2698

Deklaracja using dla "deklaracji 1' nie może współistnieć z istniejącą deklaracją using dla" deklaracji 2

Po utworzeniu [użycie — deklaracja](../../cpp/using-declaration.md) dla składowej danych, w dowolnym przy użyciu deklaracji w tym samym zakresie, który używa tej samej nazwy nie jest dozwolona, ponieważ tylko funkcje, które mogą być przeciążone.

Poniższy przykład spowoduje wygenerowanie C2698:

```
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```
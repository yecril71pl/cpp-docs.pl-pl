---
title: Błąd kompilatora C2698 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2698
dev_langs:
- C++
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7ca3e7568640aabd2b7960d97ea94a11a1d5d59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118924"
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
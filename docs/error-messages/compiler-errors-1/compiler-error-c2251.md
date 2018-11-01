---
title: Błąd kompilatora C2251
ms.date: 11/04/2016
f1_keywords:
- C2251
helpviewer_keywords:
- C2251
ms.assetid: fefe050c-f8d3-4316-b237-8007dbcdd3bf
ms.openlocfilehash: b7ffb5b8d425e74523e491827ffb8878b8e03b38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452341"
---
# <a name="compiler-error-c2251"></a>Błąd kompilatora C2251

przestrzeń nazw "namespace" nie ma składowej 'składowa' — czy chodziło Ci o "członek"?

Kompilator nie mógł znaleźć identyfikatora w określonej przestrzeni nazw.

Poniższy przykład spowoduje wygenerowanie C2251:

```
// C2251.cpp
// compile with: /c
namespace A {
   namespace B {
      void f1();
   }

   using namespace B;
}

void A::f1() {}   // C2251
void A::B::f1() {}   // OK
```
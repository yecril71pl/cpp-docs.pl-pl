---
title: Błąd kompilatora C3034
ms.date: 11/04/2016
f1_keywords:
- C3034
helpviewer_keywords:
- C3034
ms.assetid: 49db8bac-2720-4622-94e3-7988f1603fa3
ms.openlocfilehash: d0a5da87feeabc5d3d5b558ce0dd6bdfe3869d53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165570"
---
# <a name="compiler-error-c3034"></a>Błąd kompilatora C3034

Dyrektywie OpenMP "directive1", które nie może być bezpośrednio zagnieżdżona w dyrektywie "directive2"

Niektóre dyrektywy nie mogą być zagnieżdżone. Aby naprawić ten błąd, można scalić oświadczeń zarówno dyrektywy w bloku jedna dyrektywa lub możesz utworzyć kolejnych dyrektywy.

Poniższy przykład spowoduje wygenerowanie C3034:

```
// C3034.cpp
// compile with: /openmp /link vcomps.lib
int main() {

   #pragma omp single
   {
      #pragma omp single   // C3034
      {
      ;
      }
   }

   // Two consecutive single clauses are OK.
   #pragma omp single
   {
   }

   #pragma omp single
   {
   }
}
```
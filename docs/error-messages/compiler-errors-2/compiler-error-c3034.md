---
title: Błąd kompilatora C3034 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3034
dev_langs:
- C++
helpviewer_keywords:
- C3034
ms.assetid: 49db8bac-2720-4622-94e3-7988f1603fa3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e3d96e975450241a5baae60758beadfe40dbe5e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091468"
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
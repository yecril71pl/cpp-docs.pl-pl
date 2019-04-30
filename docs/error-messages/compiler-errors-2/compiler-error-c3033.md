---
title: Błąd kompilatora C3033
ms.date: 11/04/2016
f1_keywords:
- C3033
helpviewer_keywords:
- C3033
ms.assetid: 8628b6bb-a650-4ed2-af13-57acd2f7ddbb
ms.openlocfilehash: 57c2cc120a5c155d02e0e601dc2ff8924badbe67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400373"
---
# <a name="compiler-error-c3033"></a>Błąd kompilatora C3033

"var": zmienna w klauzuli "klauzula" nie może posiadać kwalifikowanego typu const

Nie może być wartości przekazane do niektórych klauzul `const` zmiennych.

Poniższy przykład spowoduje wygenerowanie C3033:

```
// C3033.cpp
// compile with: /openmp /link vcomps.lib
int main() {
   const int val = 1;
   int val2 = 1;

   #pragma omp parallel reduction(+ : val)   // C3033
   ;

   #pragma omp parallel reduction(+ : val2)   // OK
   ;
}
```
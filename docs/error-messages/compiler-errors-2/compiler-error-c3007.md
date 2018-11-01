---
title: Błąd kompilatora C3007
ms.date: 11/04/2016
f1_keywords:
- C3007
helpviewer_keywords:
- C3007
ms.assetid: e415ef42-bdc9-4f32-8198-5e25b289a089
ms.openlocfilehash: 551fb458ee02e29ae54aeb3382b2016da731808a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630463"
---
# <a name="compiler-error-c3007"></a>Błąd kompilatora C3007

"argument": klauzula w dyrektywie OpenMP "dyrektywa" nie przyjmuje argumentu

OpenMP — dyrektywa miał argumentu, ale dyrektywa nie przyjmuje argumentu.

Poniższy przykład spowoduje wygenerowanie C3007:

```
// C3007.c
// compile with: /openmp
int main()
{
   #pragma omp parallel for ordered(2)   // C3007
}
```
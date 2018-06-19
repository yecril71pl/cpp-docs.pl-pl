---
title: C3039 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3039
dev_langs:
- C++
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bdcfa36d270dc842eec0508969c650e7b30bee4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243727"
---
# <a name="compiler-error-c3039"></a>C3039 błąd kompilatora
"var": zmienna index w OpenMP instrukcji "for" nie może być zmienną redukcyjną  
  
 Zmienna index jest niejawnie prywatne, więc nie można użyć zmiennej w [redukcji](../../parallel/openmp/reference/reduction.md) w otaczającej klauzuli [równoległych](../../parallel/openmp/reference/parallel.md) dyrektywy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3039:  
  
```  
// C3039.cpp  
// compile with: /openmp /c  
int g_i;  
  
int main() {  
   int i;  
  
   #pragma omp parallel reduction(+: i)  
   {  
      #pragma omp for  
      for (i = 0; i < 10; ++i)   // C3039  
         g_i += i;  
   }  
}  
```
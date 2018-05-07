---
title: C3009 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3009
dev_langs:
- C++
helpviewer_keywords:
- C3009
ms.assetid: aded5985-f5fd-4c3e-a157-16be55ec1313
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d96fe2eea79f1b5c292664bf13b70c8bde945c7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3009"></a>C3009 błąd kompilatora
"etykieta": skok do strukturalnego bloku OpenMP jest niedozwolony  
  
 Kod nie można przeskoczyć do lub z bloku OpenMP.  
  
 Poniższy przykład generuje C3009:  
  
```  
// C3009.c  
// compile with: /openmp  
int main() {  
   #pragma omp parallel   
   {  
   lbl2:;  
   }  
   goto lbl2;   // C3009  
}  
```
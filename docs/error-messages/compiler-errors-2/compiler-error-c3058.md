---
title: C3058 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3058
dev_langs:
- C++
helpviewer_keywords:
- C3058
ms.assetid: 669d08c8-0b58-4351-88aa-c6e6e1af481c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 867dbdead4c4268035b5c34a5ef053b959c822a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246678"
---
# <a name="compiler-error-c3058"></a>C3058 błąd kompilatora
"symbol": symbol niezadeklarowany jako "threadprivate" przed jego użyciem w klauzuli "copyin"  
  
 Symbol najpierw musi zostać zadeklarowany [threadprivate](../../parallel/openmp/reference/threadprivate.md) zanim będzie można go używać w [copyin](../../parallel/openmp/reference/copyin.md) klauzuli.  
  
 Poniższy przykład generuje C3058:  
  
```  
// C3058.cpp  
// compile with: /openmp  
int x, y, z;  
#pragma omp threadprivate(x, z)  
  
void test() {  
   #pragma omp parallel copyin(x, y)   // C3058  
   {  
   }  
}  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C3058b.cpp  
// compile with: /openmp /LD  
int x, y, z;  
#pragma omp threadprivate(x, y)  
  
void test() {  
   #pragma omp parallel copyin(x, y)  
   {  
   }  
}  
```
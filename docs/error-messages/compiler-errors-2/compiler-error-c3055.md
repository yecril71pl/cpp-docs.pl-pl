---
title: "C3055 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3055
dev_langs: C++
helpviewer_keywords: C3055
ms.assetid: 60446ee0-18dd-48fc-9059-f0a14229dce8
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d7a8992a34eaf278b45e76b8ce737ee7daca79f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3055"></a>C3055 błąd kompilatora
"symbol": symbol nie może być przywoływany przed jego użyciem w dyrektywie "threadprivate"  
  
 Odwołanie do symbolu i następnie używane w [threadprivate](../../parallel/openmp/reference/threadprivate.md) klauzuli, co jest niedozwolone.  
  
 Poniższy przykład generuje C3055:  
  
```  
// C3055.cpp  
// compile with: /openmp  
int x, y;  
int z = x;  
#pragma omp threadprivate(x, y)   // C3055  
  
void test() {  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
}  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C3055b.cpp  
// compile with: /openmp /LD  
int x, y, z;  
#pragma omp threadprivate(x, y)  
  
void test() {  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
}  
```
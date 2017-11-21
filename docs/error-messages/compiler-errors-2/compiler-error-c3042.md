---
title: "C3042 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3042
dev_langs: C++
helpviewer_keywords: C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f0fe35a4021cca6ac1e3dd9846a3c165f50797f4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3042"></a>C3042 błąd kompilatora
klauzule "copyprivate" i "nowait" nie mogą występować razem w dyrektywie OpenMP "dyrektywy"  
  
 [Copyprivate](../../parallel/openmp/reference/copyprivate.md) i [nowait](../../parallel/openmp/reference/nowait.md) klauzule wzajemnie się wykluczają na określonym dyrektywy. Aby naprawić ten błąd, Usuń jedno lub oba `copyprivate` lub `nowait` klauzul.  
  
 Poniższy przykład generuje C3042:  
  
```  
// C3042.cpp  
// compile with: /openmp /c  
#include <stdio.h>  
#include "omp.h"  
  
double d;  
  
int main() {  
    #pragma omp parallel private(d)  
   {  
      #pragma omp single copyprivate(d) nowait   // C3042  
      {  
      }  
   }  
}  
```
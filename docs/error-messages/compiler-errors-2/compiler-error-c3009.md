---
title: "C3009 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3009
dev_langs: C++
helpviewer_keywords: C3009
ms.assetid: aded5985-f5fd-4c3e-a157-16be55ec1313
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e005fc24ee9b8325215709cf5728315cb7c7d9ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
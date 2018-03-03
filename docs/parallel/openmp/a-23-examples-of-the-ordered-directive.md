---
title: "Przykłady A.23 uporządkowanej dyrektywy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 83d77bb4f064a7ee69b013b36de919b57486b3e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23   Przykłady dyrektyw uporządkowanych
Istnieje możliwość uporządkowane sekcje z `for` określenia `ordered` klauzuli. Pierwszym przykładzie jest niezgodne, ponieważ interfejsu API określa następujące czynności:  
  
 "Iteracji pętli z `for` konstrukcja nie należy wykonać takie same `ordered` dyrektywy więcej niż jeden raz, a nie musisz wykonać więcej niż jeden `ordered` dyrektywy." (Zobacz [sekcji 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) na stronie 22)  
  
 W tym przykładzie niezgodnych wszystkich iteracji wykonaj 2 uporządkowanej sekcje:  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
}  
```  
  
 W poniższym przykładzie zgodne przedstawiono `for` z więcej niż jednym uporządkowane sekcji:  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    if (i <= 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
    (i > 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
}  
```
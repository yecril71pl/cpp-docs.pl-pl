---
title: Przykłady A.23 uporządkowanej dyrektywy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37cc4ea9db8cbd1a7bf095e2bde0ae482053a584
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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
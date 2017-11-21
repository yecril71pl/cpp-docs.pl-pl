---
title: A.12 atomic Dyrektywa Using | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 12c6467ee3233ce5d36d131ec81072bab8b841fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="a12---using-the-atomic-directive"></a>A.12   Użycie dyrektywy niepodzielnej
Poniższy przykład pozwala uniknąć wyścigu (aktualizacje jednoczesne elementu *x* przez wiele wątków) przy użyciu `atomic` — dyrektywa ([sekcji 2.6.4 —](../../parallel/openmp/2-6-4-atomic-construct.md) na stronie 19):  
  
```  
#pragma omp parallel for shared(x, y, index, n)  
    for (i=0; i<n; i++)   
    {  
        #pragma omp atomic  
            x[index[i]] += work1(i);  
        y[i] += work2(i);  
    }  
```  
  
 Zaletą używania `atomic` dyrektywy w tym przykładzie jest możliwość aktualizacji dwóch różnych elementów x są wykonywane równolegle. Jeśli `critical` — dyrektywa ([sekcji 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) na stronie 18) były używane, a następnie aktualizuje wszystkie elementy *x* będzie wykonywane szeregowo (choć nie w żadnym gwarantowana kolejności).  
  
 Należy pamiętać, że `atomic` dyrektywy dotyczy tylko w instrukcji języka C lub C++, natychmiast po jej.  W rezultacie elementy *y* nie są automatycznie aktualizowane w tym przykładzie.
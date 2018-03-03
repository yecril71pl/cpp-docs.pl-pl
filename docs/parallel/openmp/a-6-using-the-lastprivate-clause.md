---
title: "Przy użyciu lastprivate klauzuli A.6 | Dokumentacja firmy Microsoft"
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
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1744787e1dfb90fa9af93db5dba4eecd600b4334
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6   Użycie klauzuli ostatniej prywatnej
Czasami prawidłowe wykonanie zależy od wartości przypisującej ostatnich iteracji pętli do zmiennej. Programów, które musi zawierać takie zmienne jako argumenty do `lastprivate` klauzuli ([sekcji 2.7.2.3 ostatnia](../../parallel/openmp/2-7-2-3-lastprivate.md) na stronie 27) tak, aby wartości zmiennych są takie same jak podczas pętli jest wykonywane sekwencyjnie.  
  
```  
#pragma omp parallel  
{  
   #pragma omp for lastprivate(i)  
      for (i=0; i<n-1; i++)  
         a[i] = b[i] + b[i+1];  
}  
a[i]=b[i];  
```  
  
 W powyższym przykładzie wartość `i` na końcu równoległego regionu będzie równa `n-1`, jak w przypadku sekwencyjnych.
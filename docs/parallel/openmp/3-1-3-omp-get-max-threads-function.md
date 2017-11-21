---
title: 3.1.3 funkcja omp_get_max_threads | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e021f0873aa94f53a1218a3278a744a0c7740e65
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="313-ompgetmaxthreads-function"></a>3.1.3 Funkcja omp_get_max_threads
**Omp_get_max_threads** funkcja zwróci liczbę całkowitą, która może być przynajmniej tak duże jak liczba wątków, które będzie używane do utworzenia zespołu, jeśli równoległego regionu bez **num_threads** — klauzula zostały w tym momencie występujących w kodzie. Format jest następujący:  
  
```  
#include <omp.h>  
int omp_get_max_threads(void);  
```  
  
 Następujące wyraża dolna granica wartości liczby **omp_get_max_threads**:  
  
```  
  
threads-used-for-next-team  
 <= omp_get_max_threads  
  
```  
  
 Należy pamiętać, że jeśli kolejne równoległego regionu używa **num_threads** klauzuli poproś o określoną liczbę wątków, gwarancji na dolna granica wynik **omp_get_max_threads** nie długich blokad.  
  
 **Omp_get_max_threads** wartość zwracana przez funkcję można dynamicznie przydzielić wystarczającej ilości miejsca dla wszystkich wątków w zespole na kolejnych równoległego regionu.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   **omp_get_num_threads** funkcji, zobacz [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37.  
  
-   **omp_set_num_threads** funkcji, zobacz [sekcji 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stronie 36.  
  
-   **omp_set_dynamic** funkcji, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.  
  
-   **num_threads** klauzuli, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.
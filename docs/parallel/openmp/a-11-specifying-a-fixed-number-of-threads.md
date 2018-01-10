---
title: "Określanie stałej liczby wątków A.11 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 72c8aca2b90f021771ba9f9fc8a86d784ffe24a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="a11---specifying-a-fixed-number-of-threads"></a>A.11   Określanie stałej liczby wątków
Niektóre programy polegają na stałe, prespecified liczbę wątków wykonane nieprawidłowo.  Ustawieniem domyślnym dynamiczne Dostosowywanie to liczba wątków jest zdefiniowane w implementacji, programów, które można wyłączyć możliwość dynamicznego wątków i ustaw liczbę wątków jawnie zapewniające przenośność. Poniższy przykład pokazuje, jak to zrobić przy użyciu `omp_set_dynamic` ([sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39), i `omp_set_num_threads` ([sekcji 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stronie 36):  
  
```  
omp_set_dynamic(0);  
omp_set_num_threads(16);  
#pragma omp parallel shared(x, npoints) private(iam, ipoints)  
{  
    if (omp_get_num_threads() != 16)   
      abort();  
    iam = omp_get_thread_num();  
    ipoints = npoints/16;  
    do_by_16(x, iam, ipoints);  
}  
```  
  
 W tym przykładzie program wykonuje poprawnie tylko wtedy, gdy jest wykonywana przez wątki 16. Jeśli nie może obsłużyć 16 wątków implementacji, w tym przykładzie jest zdefiniowane w implementacji.  
  
 Należy pamiętać, że liczba wątków wykonywania równoległego regionu pozostaje stała podczas równoległego regionu, niezależnie od tego, wątki dynamiczne ustawienia. Mechanizm dynamicznej wątków określa liczbę wątków używanych na początku równoległego regionu i utrzymuje stały czas trwania regionu.
---
title: "A.15 określającą liczbę wątków używanych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e8b7fb8cf6218863287d582a097cb43b399cff07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15   Określanie liczby wykorzystywanych wątków
Rozważmy następujący przykład niepoprawne (dla [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37):  
  
```  
np = omp_get_num_threads(); // misplaced   
#pragma omp parallel for schedule(static)  
    for (i=0; i<np; i++)  
        work(i);  
```  
  
 `omp_get_num_threads()` Wywołanie zwraca wartość 1 w serial sekcji kodu, więc *potoki* będzie zawsze równa 1 w poprzednim przykładzie. Aby ustalić liczbę wątków, które zostaną wdrożone do równoległego regionu, wywołanie powinien znajdować się wewnątrz równoległego regionu.  
  
 Poniższy przykład przedstawia sposób ponownego zapisywania tego programu, bez uwzględniania zapytanie to liczba wątków:  
  
```  
#pragma omp parallel private(i)  
{  
    i = omp_get_thread_num();  
    work(i);  
}  
```
---
title: 3.3.1 funkcja omp_get_wtime | Dokumentacja firmy Microsoft
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
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f89a71d1b91a27dfdd0abf13be4a5f0e30b3fd9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="331-ompgetwtime-function"></a>3.3.1 Funkcja omp_get_wtime
`omp_get_wtime` Gettotalsize() zwróciło wartość punktu zmiennoprzecinkowe podwójnej precyzji czas zegarowy czas w sekundach, ponieważ niektóre "czas w przeszłości".  Rzeczywisty "czas w przeszłości" jest dowolnego, ale będzie gwarancji, nie należy zmieniać podczas wykonywania programu aplikacji. Format jest następujący:  
  
```  
#include <omp.h>  
double omp_get_wtime(void);  
```  
  
 Przewiduje się, że funkcja będzie służyć do pomiaru czas, jak pokazano w poniższym przykładzie:  
  
```  
double start;  
double end;  
start = omp_get_wtime();  
... work to be timed ...  
end = omp_get_wtime();  
printf_s("Work took %f sec. time.\n", end-start);  
```  
  
 Godziny są zwracane są "dla każdego wątku razy", przez które mają się, że nie muszą być globalnie spójne we wszystkich wątków uczestniczących w aplikacji.
---
title: omp_set_dynamic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_set_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_set_dynamic OpenMP function
ms.assetid: 3845faf2-a0ca-45a5-ae70-2a7a6164f1e8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00ee1ad4c42e0d2f1303854cbd050e5601d0c3cd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ompsetdynamic"></a>omp_set_dynamic
Wskazuje, że liczba wątków, które są dostępne w kolejnych równoległego regionu można dostosować w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_set_dynamic(  
   int val  
);  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `val`  
 Wartość, która wskazuje, czy liczba wątków, które są dostępne w kolejnych równoległego regionu można dostosować w czasie wykonywania.  Jeśli jest niezerowa środowiska uruchomieniowego można dostosować liczbę wątków, jeśli zero środowiska uruchomieniowego nie będzie dynamicznie dostosowywane to liczba wątków.  
  
## <a name="remarks"></a>Uwagi  
 Liczba wątków nigdy nie przekroczy wartość ustawioną przez [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) lub [OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md).  
  
 Użyj [omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md) Aby wyświetlić bieżące ustawienie `omp_set_dynamic`.  
  
 Ustawienie `omp_set_dynamic` zastąpią ustawienia [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md) zmiennej środowiskowej.  
  
 Aby uzyskać więcej informacji, zobacz [3.1.7 funkcja omp_set_dynamic](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).  
  
## <a name="example"></a>Przykład  
  
```  
// omp_set_dynamic.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main()   
{  
    omp_set_dynamic(9);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_dynamic( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_dynamic( ));  
        }  
}  
```  
  
```Output  
1  
1  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
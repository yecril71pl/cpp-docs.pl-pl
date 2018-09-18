---
title: omp_set_dynamic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_set_dynamic OpenMP function
ms.assetid: 3845faf2-a0ca-45a5-ae70-2a7a6164f1e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3e8ac574ce304238affbab41acc415e1d8de697
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026910"
---
# <a name="ompsetdynamic"></a>omp_set_dynamic
Wskazuje, że liczba wątków, które są dostępne w kolejnych równoległego regionu można dostosować w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_set_dynamic(  
   int val  
);  
```  
  
### <a name="parameters"></a>Parametry
  
*Val*<br/>
Wartość, która wskazuje, jeśli liczba wątków, które są dostępne w kolejnych równoległego regionu można dostosować w czasie wykonywania.  Jeśli wartość jest niezerowa, środowisko uruchomieniowe, które można dostosować liczbę wątków, jeśli zero, środowisko wykonawcze nie dynamicznie dostosowuje liczbę wątków.  
  
## <a name="remarks"></a>Uwagi  
 Liczba wątków nigdy nie przekroczy wartość ustawioną przy użyciu [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) lub [OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md).  
  
 Użyj [omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md) do wyświetlenia bieżącego ustawienia `omp_set_dynamic`.  
  
 Ustawienie `omp_set_dynamic` spowoduje przesłonięcie ustawień [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md) zmiennej środowiskowej.  
  
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
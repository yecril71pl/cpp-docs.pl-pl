---
title: sekcje (OpenMP) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- section
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- sections OpenMP directive
ms.assetid: 4cd1d776-e198-470e-930a-01fb0ab0a0bd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9cdc8a79f95f2a2a4dee3c43c067177f0924b46f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="sections-openmp"></a>sekcje (OpenMP)
Identyfikuje sekcji kodu do podzielony wszystkie wątki.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma omp [parallel] sections [clauses]  
{  
   #pragma omp section  
   {  
      code_block   
   }   
}  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `clause` (opcjonalnie)  
 Klauzule zero lub więcej. Zobacz sekcję uwag listę klauzule obsługiwane przez **sekcje**.  
  
## <a name="remarks"></a>Uwagi  
 **Sekcje** dyrektywa może zawierać zero lub więcej **sekcji** dyrektywy.  
  
 **Sekcje** dyrektywy obsługuje następujące klauzule OpenMP:  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [lastprivate](../../../parallel/openmp/reference/lastprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
 Jeśli **równoległych** jest określona, `clause` może zostać klauzuli zaakceptowane przez **równoległych** lub **sekcje** dyrektywy, z wyjątkiem `nowait`.  
  
 Aby uzyskać więcej informacji, zobacz [2.4.2 — konstrukcja sekcji](../../../parallel/openmp/2-4-2-sections-construct.md).  
  
## <a name="example"></a>Przykład  
  
```  
// omp_sections.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
    #pragma omp parallel sections num_threads(4)  
    {  
        printf_s("Hello from thread %d\n", omp_get_thread_num());  
        #pragma omp section  
        printf_s("Hello from thread %d\n", omp_get_thread_num());  
    }  
}  
```  
  
```Output  
Hello from thread 0  
Hello from thread 0  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)
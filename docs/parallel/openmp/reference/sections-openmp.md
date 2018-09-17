---
title: sekcje (OpenMP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- section
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- sections OpenMP directive
ms.assetid: 4cd1d776-e198-470e-930a-01fb0ab0a0bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3b369cfbd68edd32b644c9a4ec0520329507b6e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708035"
---
# <a name="sections-openmp"></a>sekcje (OpenMP)
Identyfikuje sekcje kodu w celu podzielone między wszystkie wątki.  
  
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
  
## <a name="arguments"></a>Argumenty

*Klauzula*<br/>
(Opcjonalnie) Zero lub więcej klauzul. Zobacz sekcję Spostrzeżenia, aby uzyskać listę klauzul obsługiwane przez **sekcje**.

## <a name="remarks"></a>Uwagi  
 **Sekcje** dyrektywy może zawierać zero lub więcej **sekcji** dyrektywy.  
  
 **Sekcje** dyrektywy obsługuje następujące klauzule OpenMP:  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [lastprivate](../../../parallel/openmp/reference/lastprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
 Jeśli **równoległe** również jest określony, `clause` mogą być klauzuli akceptowane przez **równoległe** lub **sekcje** dyrektyw, z wyjątkiem `nowait`.  
  
 Aby uzyskać więcej informacji, zobacz [2.4.2 konstrukcja sections](../../../parallel/openmp/2-4-2-sections-construct.md).  
  
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
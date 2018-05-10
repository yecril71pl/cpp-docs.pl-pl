---
title: pojedynczy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Single
dev_langs:
- C++
helpviewer_keywords:
- single OpenMP directive
ms.assetid: 85cf94fb-cb9c-4d82-8609-adffa9f552e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6dd5349331ac23998511a8f1b838d2cd13b01998
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="single"></a>pojedyncze
Umożliwia określenie, czy mają zostać wykonane sekcji kodu w jednym wątku, niekoniecznie głównego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma omp single [clauses]   
{  
   code_block   
}  
```  
  
#### <a name="parameters"></a>Parametry  
 `clause` (opcjonalnie)  
 Klauzule zero lub więcej. Zobacz sekcję uwag listę klauzule obsługiwane przez **pojedynczego**.  
  
## <a name="remarks"></a>Uwagi  
 **Pojedynczego** dyrektywy obsługuje następujące klauzule OpenMP:  
  
-   [copyprivate](../../../parallel/openmp/reference/copyprivate.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
 [Wzorca](../../../parallel/openmp/reference/master.md) dyrektywy pozwala określić, że sekcji kodu mają zostać wykonane tylko w głównym wątku.  
  
 Aby uzyskać więcej informacji, zobacz [skonstruować 2.4.3 pojedynczego](../../../parallel/openmp/2-4-3-single-construct.md).  
  
## <a name="example"></a>Przykład  
  
```  
// omp_single.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(2)  
   {  
      #pragma omp single  
      // Only a single thread can read the input.  
      printf_s("read input\n");  
  
      // Multiple threads in the team compute the results.  
      printf_s("compute results\n");  
  
      #pragma omp single  
      // Only a single thread can write the output.  
      printf_s("write output\n");  
    }  
}  
```  
  
```Output  
read input  
compute results  
compute results  
write output  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)
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
ms.openlocfilehash: 8a57d93d8d2be84a470dd48d1ca6f9b04010182f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020982"
---
# <a name="single"></a>pojedyncze
Pozwala określić, że sekcji kodu powinna zostać wykonana w jednym wątku, niekoniecznie głównego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma omp single [clauses]   
{  
   code_block   
}  
```  
  
#### <a name="parameters"></a>Parametry  

*Klauzula*<br/>
(Opcjonalnie) Zero lub więcej klauzul. Zobacz sekcję Spostrzeżenia, aby uzyskać listę klauzul obsługiwane przez **pojedynczego**.  
  
## <a name="remarks"></a>Uwagi  
 **Pojedynczego** dyrektywy obsługuje następujące klauzule OpenMP:  
  
-   [copyprivate](../../../parallel/openmp/reference/copyprivate.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
[Wzorca](../../../parallel/openmp/reference/master.md) dyrektywy pozwala określić, że część kodu mają zostać wykonane tylko w wątku głównym.  
  
 Aby uzyskać więcej informacji, zobacz [konstruowania 2.4.3 pojedynczego](../../../parallel/openmp/2-4-3-single-construct.md).  
  
## <a name="example"></a>Przykład  
  
```cpp  
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
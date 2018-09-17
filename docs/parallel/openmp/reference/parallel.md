---
title: równoległe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- parallel
dev_langs:
- C++
helpviewer_keywords:
- parallel OpenMP directive
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c8b1466eae343b6c644b6ecfbd919c3241259bf
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705968"
---
# <a name="parallel"></a>równoległe
Definiuje równoległego regionu, czyli kodu wykonywanego przez wiele wątków jednocześnie.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma omp parallel [clauses]  
{  
   code_block  
}  
```  
  
## <a name="arguments"></a>Argumenty

*Klauzula*<br/>
(Opcjonalnie) Zero lub więcej klauzul.  Zobacz sekcję Spostrzeżenia, aby uzyskać listę klauzul obsługiwane przez **równoległe**.  
  
## <a name="remarks"></a>Uwagi  
 **Równoległe** dyrektywy obsługuje następujące klauzule OpenMP:  
  
-   [copyin](../../../parallel/openmp/reference/copyin.md)  
  
-   [default](../../../parallel/openmp/reference/default-openmp.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [if](../../../parallel/openmp/reference/if-openmp.md)  
  
-   [num_threads](../../../parallel/openmp/reference/num-threads.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
-   [Udostępnione](../../../parallel/openmp/reference/shared-openmp.md)  
  
 **równoległe** może również służyć za pomocą [sekcje](../../../parallel/openmp/reference/sections-openmp.md) i [dla](../../../parallel/openmp/reference/for-openmp.md) dyrektywy.  
  
 Aby uzyskać więcej informacji, zobacz [2.3 konstrukcja równoległa](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ustawić liczbę wątków i zdefiniuj równoległego regionu. Domyślnie liczba wątków jest równa liczbie procesorów logicznych na maszynie. Na przykład jeśli masz maszyny z jednego procesora fizycznego, który ma włączoną wielowątkowość, ma dwa procesory logiczne, a więc dwoma wątkami.  
  
```  
// omp_parallel.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(4)  
   {  
      int i = omp_get_thread_num();  
      printf_s("Hello from thread %d\n", i);  
   }  
}  
```  
  
```Output  
Hello from thread 0  
Hello from thread 1  
Hello from thread 2  
Hello from thread 3  
```  
  
## <a name="comment"></a>Komentarz  
 Należy pamiętać, że kolejność danych wyjściowych może się różnić na różnych maszynach.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)
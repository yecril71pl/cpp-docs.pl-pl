---
title: "równoległe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: parallel
dev_langs: C++
helpviewer_keywords: parallel OpenMP directive
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 289a4928c9c46f6d758ddc2f30ed864488ab725e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="parallel"></a>równoległe
Definiuje równoległego regionu jest kod, który zostanie wykonane przez wiele wątków jednocześnie.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma omp parallel [clauses]  
{  
   code_block  
}  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `clause`(opcjonalnie)  
 Klauzule zero lub więcej.  Zobacz sekcję uwag listę klauzule obsługiwane przez **równoległych**.  
  
## <a name="remarks"></a>Uwagi  
 **Równoległych** dyrektywy obsługuje następujące klauzule OpenMP:  
  
-   [copyin](../../../parallel/openmp/reference/copyin.md)  
  
-   [domyślne](../../../parallel/openmp/reference/default-openmp.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [Jeśli](../../../parallel/openmp/reference/if-openmp.md)  
  
-   [num_threads](../../../parallel/openmp/reference/num-threads.md)  
  
-   [prywatne](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [redukcja](../../../parallel/openmp/reference/reduction.md)  
  
-   [udostępnione](../../../parallel/openmp/reference/shared-openmp.md)  
  
 **równoległe** można również używać razem [sekcje](../../../parallel/openmp/reference/sections-openmp.md) i [dla](../../../parallel/openmp/reference/for-openmp.md) dyrektywy.  
  
 Aby uzyskać więcej informacji, zobacz [2.3 konstrukcja równoległa](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ustawić liczbę wątków i zdefiniowanie równoległego regionu. Domyślnie to liczba wątków jest równa liczbie procesorów logicznych na tym komputerze. Na przykład jeśli masz maszyny z jednego procesora fizycznego, który ma treading, będzie mieć dwa procesory logiczne oraz, w związku z tym dwoma wątkami.  
  
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
 Należy pamiętać, że kolejność danych wyjściowych może różnić się na różnych komputerach.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)
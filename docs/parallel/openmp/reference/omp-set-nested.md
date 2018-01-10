---
title: omp_set_nested | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_set_nested
dev_langs: C++
helpviewer_keywords: omp_set_nested OpenMP function
ms.assetid: fa1cb08c-7b8b-42c9-8654-2c33dcffb5b6
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f08fec246b5df4b5a6dc965917e0a6438b58042f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ompsetnested"></a>omp_set_nested
Umożliwia równoległości zagnieżdżonych.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_set_nested(  
   int val  
);  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `val`  
 W przypadku różną od zera, włącza równoległości zagnieżdżonych. Jeśli zero, wyłącza równoległości zagnieżdżonych.  
  
## <a name="remarks"></a>Uwagi  
 OMP zagnieżdżone równoległości mogą być włączone z `omp_set_nested`, albo ustawiając [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md) zmiennej środowiskowej.  
  
 Ustawienie `omp_set_nested` zastąpią ustawienia `OMP_NESTED` zmiennej środowiskowej.  
  
 Po włączeniu zmiennej środowiskowej mogą być dzielone w przeciwnym razie operacyjnej programu, ponieważ liczba wątków wykładniczo zwiększa podczas zagnieżdżania równoległych regionów.  Na przykład funkcji, że recurses 6 razy o liczbie wątków OMP ustawioną 4 wymaga 4096 (4 do potęgi 6) wątki ogólnie rzecz biorąc, spowoduje zmniejszenie wydajności aplikacji, jeśli liczba wątków przekracza liczbę procesorów. Jedynym wyjątkiem jest we/wy powiązany aplikacji.  
  
 Użyj [omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md) Aby wyświetlić bieżące ustawienie `omp_set_nested`.  
  
 Aby uzyskać więcej informacji, zobacz [3.1.9 funkcja omp_set_nested](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).  
  
## <a name="example"></a>Przykład  
  
```  
// omp_set_nested.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    omp_set_nested(1);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_nested( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_nested( ));  
        }  
}  
```  
  
```Output  
1  
1  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
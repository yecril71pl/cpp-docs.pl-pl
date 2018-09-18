---
title: omp_set_nested | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_set_nested OpenMP function
ms.assetid: fa1cb08c-7b8b-42c9-8654-2c33dcffb5b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc3506c35dca469febafe21509064abc1726d633
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116902"
---
# <a name="ompsetnested"></a>omp_set_nested
Włącza równoległości zagnieżdżonych.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_set_nested(  
   int val  
);  
```  
  
### <a name="parameters"></a>Parametry
  
*Val*<br/>
Jeśli wartość jest niezerowa, umożliwia równoległości zagnieżdżonych. Jeśli zero, wyłącza równoległości zagnieżdżonych.  
  
## <a name="remarks"></a>Uwagi  
 OMP zagnieżdżone równoległość może zostać włączona przy użyciu `omp_set_nested`, lub poprzez skonfigurowanie [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md) zmiennej środowiskowej.  
  
 Ustawienie `omp_set_nested` spowoduje przesłonięcie ustawień `OMP_NESTED` zmiennej środowiskowej.  
  
 Po włączeniu zmiennej środowiskowej może przerwać program w przeciwnym razie operacyjnej, ponieważ wykładniczo zwiększa liczbę wątków podczas zagnieżdżania regionów równoległych.  Na przykład funkcja, że recurses 6 razy o liczbie wątków OMP równa 4 wymaga 4096 (4 do potęgi równej 6) wątki ogólnie rzecz biorąc, spowoduje zmniejszenie wydajności aplikacji, jeśli liczba wątków przekracza liczbę procesorów. Jedynym wyjątkiem jest operacji We/Wy powiązać aplikacji.  
  
 Użyj [omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md) do wyświetlenia bieżącego ustawienia `omp_set_nested`.  
  
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
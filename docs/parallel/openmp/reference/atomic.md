---
title: niepodzielne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- atomic
dev_langs:
- C++
helpviewer_keywords:
- atomic OpenMP directive
ms.assetid: 275e0338-cf2f-4525-97b5-696250000df7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7e9e9ecad2f6ea53e2f922799340eee47dd4a7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037492"
---
# <a name="atomic"></a>niepodzielne
Określa, że lokalizacji w pamięci, który będzie aktualizowany niepodzielne.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma omp atomic  
   expression  
```  
  
#### <a name="parameters"></a>Parametry  
*Wyrażenie*<br/>
Oświadczenie zawierające l-wartości, którego lokalizacja pamięci chcesz zapewnić ochronę przed wieloma zapisów. Aby uzyskać więcej informacji o formularzach prawne wyrażenia zobacz specyfikację OpenMP.  
  
## <a name="remarks"></a>Uwagi  
 `atomic` Dyrektywy nie obsługuje żadnych klauzule OpenMP.  
  
 Aby uzyskać więcej informacji, zobacz [konstruowania 2.6.4 atomic](../../../parallel/openmp/2-6-4-atomic-construct.md).  
  
## <a name="example"></a>Przykład  
  
```  
// omp_atomic.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
#define MAX 10  
  
int main() {  
   int count = 0;  
   #pragma omp parallel num_threads(MAX)  
   {  
      #pragma omp atomic  
      count++;  
   }  
   printf_s("Number of threads: %d\n", count);  
}  
```  
  
```Output  
Number of threads: 10  
```  
  
## <a name="see-also"></a>Zobacz też  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
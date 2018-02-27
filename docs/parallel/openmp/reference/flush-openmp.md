---
title: "opróżnianie (OpenMP) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Flush
dev_langs:
- C++
helpviewer_keywords:
- flush OpenMP directive
ms.assetid: 150ca46e-d4f7-4423-b0a4-838df40aeb67
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 531cd43ad5783ca399617f0a9a2d9967f5175e4d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="flush-openmp"></a>opróżnianie (OpenMP)
Określa, że wszystkie wątki tego samego widoku pamięci dla wszystkich obiektów udostępnionych.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma omp flush [(var)]  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `var` (opcjonalnie)  
 Rozdzielana przecinkami lista zmiennych, które reprezentują obiekty, które mają być synchronizowane. Jeśli `var` nie zostanie określony, cała pamięć jest opróżniany.  
  
## <a name="remarks"></a>Uwagi  
 **Opróżnić** dyrektywy obsługuje nie klauzule OpenMP.  
  
 Aby uzyskać więcej informacji, zobacz [2.6.5 dyrektywa opróżniania](../../../parallel/openmp/2-6-5-flush-directive.md).  
  
## <a name="example"></a>Przykład  
  
```  
// omp_flush.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
void read(int *data) {  
   printf_s("read data\n");  
   *data = 1;  
}  
  
void process(int *data) {  
   printf_s("process data\n");  
   (*data)++;  
}  
  
int main() {  
   int data;  
   int flag;  
  
   flag = 0;  
  
   #pragma omp parallel sections num_threads(2)  
   {  
      #pragma omp section  
      {  
         printf_s("Thread %d: ", omp_get_thread_num( ));  
         read(&data);  
         #pragma omp flush(data)  
         flag = 1;  
         #pragma omp flush(flag)  
         // Do more work.  
      }  
  
      #pragma omp section   
      {  
         while (!flag) {  
            #pragma omp flush(flag)  
         }  
         #pragma omp flush(data)  
  
         printf_s("Thread %d: ", omp_get_thread_num( ));  
         process(&data);  
         printf_s("data = %d\n", data);  
      }  
   }  
}  
```  
  
```Output  
Thread 0: read data  
Thread 1: process data  
data = 2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)
---
title: omp_set_num_threads | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_set_num_threads
dev_langs: C++
helpviewer_keywords: omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 49383e47c161c7cec59f3f0fb7c618f4c4924655
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads
Ustawia liczbę wątków w kolejnych regionach równoległe, chyba że zostaną zastąpione [num_threads](../../../parallel/openmp/reference/num-threads.md) klauzuli.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_set_num_threads(  
   int num_threads  
);  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `num_threads`  
 Liczba wątków w równoległego regionu.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [3.1.1 funkcja omp_set_num_threads](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md) przykład przy użyciu `omp_set_num_threads`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
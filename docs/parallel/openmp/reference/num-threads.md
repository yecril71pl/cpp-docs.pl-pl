---
title: num_threads | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- num_threads
dev_langs:
- C++
helpviewer_keywords:
- num_threads OpenMP clause
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b9d12b8216033b5ffe6499290f1c2b5742152b2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="numthreads"></a>num_threads
Ustawia liczbę wątków w zespole wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
num_threads(num)  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `num`  
 Liczba wątków  
  
## <a name="remarks"></a>Uwagi  
 `num_threads` Klauzuli ma te same funkcje co [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) funkcji.  
  
 `num_threads` ma zastosowanie do następujących dyrektyw:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Sekcje](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Aby uzyskać więcej informacji, zobacz [2.3 konstrukcja równoległa](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [równoległych](../../../parallel/openmp/reference/parallel.md) przykład przy użyciu `num_threads` klauzuli.  
  
## <a name="see-also"></a>Zobacz też  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)
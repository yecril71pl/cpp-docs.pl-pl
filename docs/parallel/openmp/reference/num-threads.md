---
title: num_threads | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- num_threads
dev_langs:
- C++
helpviewer_keywords:
- num_threads OpenMP clause
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7dd57950d083c4f89ee2aa5962ad1e07a55a9a8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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
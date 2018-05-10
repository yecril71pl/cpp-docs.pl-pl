---
title: omp_unset_lock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_unset_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_unset_lock OpenMP function
ms.assetid: 68fcb728-040b-4bad-979e-aaecb9097a4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 243ff6d2336d3e293d009f82ba4a39243e076f94
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ompunsetlock"></a>omp_unset_lock
Zwalnia blokadę.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_unset_lock(  
   omp_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `lock`  
 Zmienna typu [omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) który został zainicjowany z [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md), będących własnością przez wątek i wykonywania w funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [3.2.4 funkcje omp_unset_lock i omp_unset_nest_lock](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) przykład przy użyciu `omp_unset_lock`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
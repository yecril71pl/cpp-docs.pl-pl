---
title: omp_set_nest_lock | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_set_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_set_nest_lock OpenMP function
ms.assetid: b98ed889-ff8e-4217-a3e9-3993ed8699af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f2ae23cfd58b55881ebaa25f55d121d7ab45f3b3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ompsetnestlock"></a>omp_set_nest_lock
Bloki wątków wykonywania, dopóki blokada jest dostępna.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_set_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `lock`  
 Zmienna typu [omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) który został zainicjowany z [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md).  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [3.2.3 funkcje omp_set_lock i omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).  
  
## <a name="examples"></a>Przykłady  
 Zobacz [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) przykład przy użyciu `omp_set_nest_lock`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
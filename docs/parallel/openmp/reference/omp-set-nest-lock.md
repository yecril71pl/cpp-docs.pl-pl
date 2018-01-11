---
title: omp_set_nest_lock | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_set_nest_lock
dev_langs: C++
helpviewer_keywords: omp_set_nest_lock OpenMP function
ms.assetid: b98ed889-ff8e-4217-a3e9-3993ed8699af
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d073a932eff9a73d861902c3bb8a2ef00870e74b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
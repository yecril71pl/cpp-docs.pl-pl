---
title: omp_destroy_lock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_destroy_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_destroy_lock OpenMP function
ms.assetid: b73ab036-b76f-4e42-82ff-c89db2edf7c0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be14c2adaf371bc1da3cffee9766b90a2c7af216
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ompdestroylock"></a>omp_destroy_lock
Uninitializes blokady.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_destroy_lock(  
   omp_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `lock`  
 Zmienna typu [omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) który został zainicjowany z [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md).  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [3.2.2 funkcje omp_destroy_lock i omp_destroy_nest_lock](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) przykład przy użyciu `omp_destroy_lock`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
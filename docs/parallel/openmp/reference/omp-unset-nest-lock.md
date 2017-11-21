---
title: omp_unset_nest_lock | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_unset_nest_lock
dev_langs: C++
helpviewer_keywords: omp_unset_nest_lock OpenMP function
ms.assetid: 1721d061-3f9c-45d7-b479-a665cd0a121d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: badb7518b7fa90b39e1fb4af0ee07b27087f5e8d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ompunsetnestlock"></a>omp_unset_nest_lock
Zwalnia blokadą.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_unset_nest_lock(   
   omp_nest_lock_t *lock   
);  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `lock`  
 Zmienna typu [omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) który został zainicjowany z [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md), będących własnością przez wątek i wykonywania w funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [3.2.4 funkcje omp_unset_lock i omp_unset_nest_lock](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) przykład przy użyciu `omp_unset_nest_lock`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
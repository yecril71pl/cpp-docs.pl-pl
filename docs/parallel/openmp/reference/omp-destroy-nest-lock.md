---
title: omp_destroy_nest_lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_destroy_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_destroy_nest_lock OpenMP function
ms.assetid: 0ab1352b-668f-43dd-b441-31ec4cc53e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37ac75158705a26b10b077652f51396dcd591740
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104052"
---
# <a name="ompdestroynestlock"></a>omp_destroy_nest_lock
Deinicjuje blokadą.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_destroy_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
### <a name="parameters"></a>Parametry
  
*lock*<br/>
Zmienna typu [omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) , została zainicjowana przy użyciu [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md).  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [3.2.2 funkcje omp_destroy_lock i omp_destroy_nest_lock funkcji](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) na przykład za pomocą `omp_destroy_nest_lock`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
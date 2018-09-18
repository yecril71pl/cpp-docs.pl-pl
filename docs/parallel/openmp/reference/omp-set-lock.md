---
title: omp_set_lock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_set_lock OpenMP function
ms.assetid: ded839cb-ca19-403f-8622-eb52ce512d31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 390090b0f4bf5f8795373db9f61f8365257ee95b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024915"
---
# <a name="ompsetlock"></a>omp_set_lock
Wykonywanie wątku bloków, dopóki blokada jest dostępna.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_set_lock(  
   omp_lock_t *lock  
);  
```  
  
### <a name="parameters"></a>Parametry
  
*lock*<br/>
Zmienna typu [omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) , została zainicjowana przy użyciu [funkcje omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md).  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [3.2.3 funkcje omp_set_lock i omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).  
  
## <a name="examples"></a>Przykłady  
 Zobacz [funkcje omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) na przykład za pomocą `omp_set_lock`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
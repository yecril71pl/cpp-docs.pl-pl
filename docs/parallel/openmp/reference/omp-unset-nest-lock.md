---
title: omp_unset_nest_lock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_unset_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_unset_nest_lock OpenMP function
ms.assetid: 1721d061-3f9c-45d7-b479-a665cd0a121d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03ea941e793f8c3a9f40e0495442deb71b2ffa93
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402723"
---
# <a name="ompunsetnestlock"></a>omp_unset_nest_lock

Zwalnia blokadę zagnieżdżalnych.

## <a name="syntax"></a>Składnia

```
void omp_unset_nest_lock( 
   omp_nest_lock_t *lock 
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) , została zainicjowana przy użyciu [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)własnością wątku i wykonywanie w funkcji.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.4 funkcje omp_unset_lock i omp_unset_nest_lock funkcji](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

## <a name="example"></a>Przykład

Zobacz [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) na przykład za pomocą `omp_unset_nest_lock`.

## <a name="see-also"></a>Zobacz też

[Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
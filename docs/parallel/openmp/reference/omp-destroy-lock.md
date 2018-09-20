---
title: Funkcje omp_destroy_lock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_destroy_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_destroy_lock OpenMP function
ms.assetid: b73ab036-b76f-4e42-82ff-c89db2edf7c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 22ee3b0f262742223c57149d7e828a58910223fe
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400136"
---
# <a name="ompdestroylock"></a>omp_destroy_lock

Deinicjuje blokadę.

## <a name="syntax"></a>Składnia

```
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) , została zainicjowana przy użyciu [funkcje omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md).

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.2 funkcje omp_destroy_lock i omp_destroy_nest_lock funkcji](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

## <a name="example"></a>Przykład

Zobacz [funkcje omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) na przykład za pomocą `omp_destroy_lock`.

## <a name="see-also"></a>Zobacz też

[Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
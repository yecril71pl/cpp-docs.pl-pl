---
title: omp_set_nest_lock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_set_nest_lock OpenMP function
ms.assetid: b98ed889-ff8e-4217-a3e9-3993ed8699af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e7ca097219297038728adc3924980e8c91e25ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438590"
---
# <a name="ompsetnestlock"></a>omp_set_nest_lock

Wykonywanie wątku bloków, dopóki blokada jest dostępna.

## <a name="syntax"></a>Składnia

```
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) , została zainicjowana przy użyciu [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md).

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.3 funkcje omp_set_lock i omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

## <a name="examples"></a>Przykłady

Zobacz [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) na przykład za pomocą `omp_set_nest_lock`.

## <a name="see-also"></a>Zobacz też

[Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
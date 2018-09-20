---
title: num_threads | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- num_threads
dev_langs:
- C++
helpviewer_keywords:
- num_threads OpenMP clause
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27e39d7db36c121add3598387de52ecb878059b5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405271"
---
# <a name="numthreads"></a>num_threads

Ustawia liczbę wątków w zespole wątku.

## <a name="syntax"></a>Składnia

```
num_threads(num)
```

### <a name="parameters"></a>Parametry

*num*<br/>
Liczba wątków

## <a name="remarks"></a>Uwagi

`num_threads` Klauzuli ma taką samą funkcjonalność jak [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) funkcji.

`num_threads` mają zastosowanie do następujących dyrektywach:

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [Sekcje](../../../parallel/openmp/reference/sections-openmp.md)

Aby uzyskać więcej informacji, zobacz [2.3 konstrukcja równoległa](../../../parallel/openmp/2-3-parallel-construct.md).

## <a name="example"></a>Przykład

Zobacz [równoległe](../../../parallel/openmp/reference/parallel.md) na przykład za pomocą `num_threads` klauzuli.

## <a name="see-also"></a>Zobacz też

[Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)
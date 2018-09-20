---
title: omp_set_num_threads | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_num_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae9dbe52dba47208844b73175f20edcc591a3ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444947"
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads

Ustawia liczbę wątków w kolejnych regionach równoległych, chyba że zostaną zastąpione [num_threads](../../../parallel/openmp/reference/num-threads.md) klauzuli.

## <a name="syntax"></a>Składnia

```
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Parametry

*num_threads*<br/>
Liczba wątków w równoległego regionu.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.1 funkcja omp_set_num_threads](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

## <a name="example"></a>Przykład

Zobacz [omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md) na przykład za pomocą `omp_set_num_threads`.

## <a name="see-also"></a>Zobacz też

[Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
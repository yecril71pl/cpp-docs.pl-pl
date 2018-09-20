---
title: omp_get_dynamic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2b5a285ef019cd1752b60065f7040d9a937ce38
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389892"
---
# <a name="ompgetdynamic"></a>omp_get_dynamic

Zwraca wartość wskazującą, jeśli liczba wątków, które są dostępne w kolejnych równoległego regionu można dostosować w czasie wykonywania.

## <a name="syntax"></a>Składnia

```
int omp_get_dynamic();
```

## <a name="return-value"></a>Wartość zwracana

Jeśli wartość jest niezerowa, dynamiczne Dostosowywanie wątków jest włączona.

## <a name="remarks"></a>Uwagi

Dynamiczne Dostosowywanie wątków jest określony za pomocą [omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) i [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md).

Aby uzyskać więcej informacji, zobacz [3.1.7 funkcja omp_set_dynamic](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

## <a name="example"></a>Przykład

Zobacz [omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) na przykład za pomocą `omp_get_dynamic`.

## <a name="see-also"></a>Zobacz też

[Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
---
title: omp_get_nested | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_get_nested OpenMP function
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20a7378ba7e7f6dcec55cfe265dd0873bdc1fd38
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46371956"
---
# <a name="ompgetnested"></a>omp_get_nested

Zwraca wartość wskazującą, czy włączono równoległości zagnieżdżonych.

## <a name="syntax"></a>Składnia

```
int omp_get_nested( );
```

## <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera, zagnieżdżone równoległości jest włączona.

## <a name="remarks"></a>Uwagi

Zagnieżdżone równoległości jest określony za pomocą [omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md) i [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md).

Aby uzyskać więcej informacji, zobacz [3.1.10 funkcja omp_get_nested](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

## <a name="example"></a>Przykład

Zobacz [omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md) na przykład za pomocą `omp_get_nested`.

## <a name="see-also"></a>Zobacz też

[Funkcje](../../../parallel/openmp/reference/openmp-functions.md)
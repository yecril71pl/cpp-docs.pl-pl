---
title: OMP_DYNAMIC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_DYNAMIC
dev_langs:
- C++
helpviewer_keywords:
- OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b02a2a4d660057ab83da39add7fd32bcff3e6d90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392141"
---
# <a name="ompdynamic"></a>OMP_DYNAMIC

Określa, czy OpenMP, w czasie wykonywania można dostosować liczbę wątków w równoległego regionu.

## <a name="syntax"></a>Składnia

```
set OMP_DYNAMIC[=TRUE | =FALSE]
```

## <a name="remarks"></a>Uwagi

`OMP_DYNAMIC` Zmiennej środowiskowej, może zostać przesłonięta przez [omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) funkcji.

Wartość domyślna w implementacji Visual C++ OpenMP standard to `OMP_DYNAMIC=FALSE`.

Aby uzyskać więcej informacji, zobacz [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

## <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_DYNAMIC` zmiennej środowiskowej na wartość TRUE:

```
set OMP_DYNAMIC=TRUE
```

Następujące polecenie wyświetla bieżące ustawienie `OMP_DYNAMIC` zmienną środowiskową:

```
set OMP_DYNAMIC
```

## <a name="see-also"></a>Zobacz też

[Zmienne środowiskowe](../../../parallel/openmp/reference/openmp-environment-variables.md)
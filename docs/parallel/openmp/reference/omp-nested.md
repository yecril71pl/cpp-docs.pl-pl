---
title: OMP_NESTED | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NESTED
dev_langs:
- C++
helpviewer_keywords:
- OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c90878ce96cf1639c983be899ba13eccf1f040e8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376546"
---
# <a name="ompnested"></a>OMP_NESTED

Określa, czy zagnieżdżonych równoległości jest włączona, chyba że zagnieżdżone równoległości jest włączone lub wyłączone przy użyciu `omp_set_nested`.

## <a name="syntax"></a>Składnia

```
set OMP_NESTED[=TRUE | =FALSE]
```

## <a name="remarks"></a>Uwagi

`OMP_NESTED` Zmiennej środowiskowej, może zostać przesłonięta przez [omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md) funkcji.

Wartość domyślna w implementacji Visual C++ OpenMP standard to `OMP_DYNAMIC=FALSE`.

Aby uzyskać więcej informacji, zobacz [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

## <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_NESTED` zmiennej środowiskowej na wartość TRUE:

```
set OMP_NESTED=TRUE
```

Następujące polecenie wyświetla bieżące ustawienie `OMP_NESTED` zmienną środowiskową:

```
set OMP_NESTED
```

## <a name="see-also"></a>Zobacz też

[Zmienne środowiskowe](../../../parallel/openmp/reference/openmp-environment-variables.md)
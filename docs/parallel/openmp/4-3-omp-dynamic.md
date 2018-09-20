---
title: 4.3 OMP_DYNAMIC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c15fa9d8c9d86b736bfc577a3b17e9809ec9baaf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439201"
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

**OMP_DYNAMIC** zmiennej środowiskowej Włącza lub wyłącza dynamiczne Dostosowywanie liczby dostępnych do wykonania regionów równoległych wątków, chyba że jawnie włączona lub wyłączona przez wywołanie metody dynamiczneDostosowywanie**omp_set_dynamic** procedury biblioteki. Jego wartość musi być **TRUE** lub **FALSE**.

Jeśli ustawiono **TRUE**, liczbę wątków, które są używane do wykonywania regionów równoległych mogą być dostosowywane przez środowisko uruchomieniowe najlepsze wykorzystanie zasobów systemowych.  Jeśli ustawiono **FALSE**, dynamiczne Dostosowywanie jest wyłączona. Stan domyślny jest zdefiniowane w implementacji.

Przykład:

```
setenv OMP_DYNAMIC TRUE
```

## <a name="cross-references"></a>Odsyłacze:

- Aby uzyskać więcej informacji na temat regionów równoległych, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.

- **omp_set_dynamic** funkcji, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.
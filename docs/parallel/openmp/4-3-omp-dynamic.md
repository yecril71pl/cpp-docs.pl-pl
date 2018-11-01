---
title: 4.3 OMP_DYNAMIC
ms.date: 11/04/2016
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
ms.openlocfilehash: 0ea6784159a11fc194d0c1cd16d2316a80b9cd37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488572"
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
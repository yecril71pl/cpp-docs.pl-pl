---
title: 3.1.8 Funkcja omp_get_dynamic
ms.date: 11/04/2016
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
ms.openlocfilehash: d9476894e5aff4cc7bb9c67fbbeb14d185b65f5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566429"
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 Funkcja omp_get_dynamic

**Omp_get_dynamic** funkcja zwraca wartość różną od zera, jeśli dynamiczne Dostosowywanie wątków jest włączona, a w przeciwnym razie zwraca wartość 0. Format jest następujący:

```
#include <omp.h>
int omp_get_dynamic(void);
```

Jeśli wdrożenia nie implementuje dynamiczne Dostosowywanie liczby wątków, ta funkcja zawsze zwraca wartość 0.

## <a name="cross-references"></a>Odsyłacze:

- Opis wątku dynamicznego dostosowania, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.
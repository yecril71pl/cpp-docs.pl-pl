---
title: 3.1.8 funkcja omp_get_dynamic | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c30f49eaf91353d6a7cd9bd26e0e10e95cb6acd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426786"
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
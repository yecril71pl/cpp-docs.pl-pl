---
title: 3.1.9 funkcja omp_set_nested | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68e5898b8b57814a152ca2ce9ced84a9df8190cc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414542"
---
# <a name="319-ompsetnested-function"></a>3.1.9 Funkcja omp_set_nested

**Omp_set_nested** funkcji włącza lub wyłącza równoległości zagnieżdżonych. Format jest następujący:

```
#include <omp.h>
void omp_set_nested(int nested);
```

Jeśli *zagnieżdżonych* wynikiem jest 0, zagnieżdżone równoległości jest wyłączone, co jest ustawieniem domyślnym i zagnieżdżone regionów równoległych są serializowane i wykonywane przez bieżący wątek. Jeśli *zagnieżdżonych* oblicza wartość różną od zera, zagnieżdżonych równoległości jest włączona i regionów równoległych, które są zagnieżdżone mogą wdrażać dodatkowe wątki w celu utworzenia zagnieżdżonych zespołów.

Funkcja ta ma wpływ opisanych powyżej, gdy wywoływana z części programu gdzie **omp_in_parallel** funkcja zwraca wartość zero. Jeśli zostanie wywołana z części programu gdzie **omp_in_parallel** funkcja zwraca wartość różną od zera, zachowanie tej funkcji jest niezdefiniowane.

To wywołanie ma pierwszeństwo przed **OMP_NESTED** zmiennej środowiskowej.

Po włączeniu zagnieżdżonych równoległości liczba wątków używanych do wykonywania zagnieżdżonych regionów równoległych jest zdefiniowane w implementacji. Co w efekcie CLS OpenMP implementacje są dozwolone do serializacji zagnieżdżonych regionów równoległych, nawet wtedy, gdy zagnieżdżony równoległości jest włączona.

## <a name="cross-references"></a>Odsyłacze:

- **OMP_NESTED** środowiska zmiennych, zobacz [4.4 sekcji](../../parallel/openmp/4-4-omp-nested.md) na stronie 49.

- **omp_in_parallel** funkcji, zobacz [sekcji 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) na stronie 38.
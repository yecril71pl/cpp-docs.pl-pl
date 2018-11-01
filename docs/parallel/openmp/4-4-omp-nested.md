---
title: 4.4 OMP_NESTED
ms.date: 11/04/2016
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
ms.openlocfilehash: e45b8901c56923ab37ca387a5f057c5b41af21f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453628"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED

`OMP_NESTED` Zmiennej środowiskowej Włącza lub wyłącza zagnieżdżonych równoległości, chyba że zagnieżdżone równoległości jest włączone lub wyłączone przez wywołanie metody `o` **mp_set_nested** procedury biblioteki. Jeśli ustawiona na **TRUE**, zagnieżdżone równoległości jest włączony; Jeśli jest równa **FALSE**, zagnieżdżone równoległości jest wyłączona. Wartość domyślna to **FALSE**.

Przykład:

```
setenv OMP_NESTED TRUE
```

## <a name="cross-reference"></a>Granic odwołania:

- `omp_set_nested` funkcji, zobacz [sekcji 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stronie 40.
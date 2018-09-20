---
title: 4.4 OMP_NESTED | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1083269f31ebc710da24430635ff8381e3f2147a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419519"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED

`OMP_NESTED` Zmiennej środowiskowej Włącza lub wyłącza zagnieżdżonych równoległości, chyba że zagnieżdżone równoległości jest włączone lub wyłączone przez wywołanie metody `o` **mp_set_nested** procedury biblioteki. Jeśli ustawiona na **TRUE**, zagnieżdżone równoległości jest włączony; Jeśli jest równa **FALSE**, zagnieżdżone równoległości jest wyłączona. Wartość domyślna to **FALSE**.

Przykład:

```
setenv OMP_NESTED TRUE
```

## <a name="cross-reference"></a>Granic odwołania:

- `omp_set_nested` funkcji, zobacz [sekcji 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stronie 40.
---
title: 4.1 OMP_SCHEDULE
ms.date: 11/04/2016
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
ms.openlocfilehash: 4731299a4f7203dd01f660ea25bf2f5b58060630
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432698"
---
# <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE

**OMP_SCHEDULE** ma zastosowanie tylko do **dla** i **równoległe w** dyrektyw, które mają typ harmonogramu **środowiska uruchomieniowego**. Rozmiar typu i fragmentów harmonogram dla wszystkich takich pętli można ustawić w czasie wykonywania przez ustawienie tej zmiennej środowiskowej, do dowolnego typu harmonogramu rozpoznany i opcjonalnie *chunk_size*.

Dla **dla** i **równoległe w** dyrektyw, które mają inny niż typ harmonogramu **środowiska uruchomieniowego**, **OMP_SCHEDULE** jest ignorowana. Wartością domyślną dla tej zmiennej środowiskowej jest zdefiniowane w implementacji. Jeśli opcjonalny *chunk_size* jest ustawiona, wartość musi być dodatnia. Jeśli *chunk_size* nie jest ustawiona, przyjmowana jest wartość 1, z wyjątkiem w przypadku właściwości **statyczne** harmonogramu. Aby uzyskać **statyczne** harmonogram, domyślny rozmiar fragmentu jest ustawiony do obszaru iteracji pętli dzielona przez liczbę wątków stosowane do pętli.

Przykład:

```
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

## <a name="cross-references"></a>Odsyłacze:

- **Aby uzyskać** dyrektywy, zobacz [sekcji 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stronie 11.

- **równoległe w** dyrektywy, zobacz [sekcji 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) na stronie 16.
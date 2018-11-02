---
title: 2.5.2 Konstrukcja sekcji równoległych
ms.date: 11/04/2016
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
ms.openlocfilehash: 1b74dacb9730a14364d7202918ae195cbf691955
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533669"
---
# <a name="252-parallel-sections-construct"></a>2.5.2 Konstrukcja sekcji równoległych

**Sekcji równoległych** postaci skrótów zapewnia dyrektywa określająca **równoległe** zawierające tylko jeden region **sekcje** dyrektywy. Semantyka są takie same jak jawne określenie **równoległe** dyrektywy bezpośrednio następuje **sekcje** dyrektywy. Składnia **sekcji równoległych** dyrektywy jest następująca:

```
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*Klauzuli* może być jedną z klauzul zaakceptowane przez **równoległe** i **sekcje** dyrektyw, z wyjątkiem **nowait** klauzuli.

## <a name="cross-references"></a>Odsyłacze:

- **równoległe** dyrektywy, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.

- **sekcje** dyrektywy, zobacz [sekcji 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) na stronie 14.
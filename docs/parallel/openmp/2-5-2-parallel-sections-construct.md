---
title: 2.5.2 konstrukcja parallel sections | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 073d0561fe4bfbb96ed88681a077da6fc985c963
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402333"
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
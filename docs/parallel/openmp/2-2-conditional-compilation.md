---
title: 2.2 Kompilacja warunkowa
ms.date: 11/04/2016
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
ms.openlocfilehash: 9dc107ee9e5328df205d4b6f826f71c23abfb3ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658552"
---
# <a name="22-conditional-compilation"></a>2.2 Kompilacja warunkowa

_**OPENMP** Nazwa makra jest zdefiniowany przez implementacje CLS OpenMP jako stałej dziesiętnej *yyyymm*, który będzie stanowić rok i miesiąc specyfikacji zatwierdzone. To makro nie może być przedmiotem **#define** lub **#undef** dyrektywy preprocesora.

```
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Jeśli dostawców zdefiniować rozszerzenia OpenMP, ich mogą określać dodatkowe wstępnie zdefiniowanych makr.
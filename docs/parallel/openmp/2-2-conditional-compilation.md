---
title: 2.2 kompilacja warunkowa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25b52ce624777efe85e27b8ce5e7941bc2f5dcba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440384"
---
# <a name="22-conditional-compilation"></a>2.2 Kompilacja warunkowa

_**OPENMP** Nazwa makra jest zdefiniowany przez implementacje CLS OpenMP jako stałej dziesiętnej *yyyymm*, który będzie stanowić rok i miesiąc specyfikacji zatwierdzone. To makro nie może być przedmiotem **#define** lub **#undef** dyrektywy preprocesora.

```
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Jeśli dostawców zdefiniować rozszerzenia OpenMP, ich mogą określać dodatkowe wstępnie zdefiniowanych makr.
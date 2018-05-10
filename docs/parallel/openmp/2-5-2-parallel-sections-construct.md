---
title: 2.5.2 konstrukcja sekcji równoległych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b6f7a84e322cb273733c6a724ee2563928df8362
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="252-parallel-sections-construct"></a>2.5.2 Konstrukcja sekcji równoległych
**Sekcji równoległych** dyrektywa zawiera formularza skrótów w celu określenia **równoległych** zawierających tylko jeden region **sekcje** dyrektywy. Semantyka są takie same jak jawne określenie **równoległych** dyrektywy poprzedzającą **sekcje** dyrektywy. Składnia **sekcji równoległych** dyrektywy wygląda następująco:  
  
```  
#pragma omp parallel sections  [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-linestructured-block  ]  
   ...  
}  
```  
  
 *Klauzuli* może być jedną z klauzul zaakceptowane przez **równoległych** i **sekcje** dyrektywy, z wyjątkiem **nowait** klauzuli.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   **równoległe** dyrektywy, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.  
  
-   **sekcje** dyrektywy, zobacz [sekcji 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) na stronie 14.
---
title: "2.5.2 konstrukcja sekcji równoległych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e3a76a950d547effccf0b50fa04799814597bc5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
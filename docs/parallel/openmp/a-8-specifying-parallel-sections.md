---
title: A.8 określanie sekcji równoległych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acb28f4e7e99ea09696d116ab031778fcf9ff919
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="a8---specifying-parallel-sections"></a>A.8   Określanie sekcji równoległych
W poniższym przykładzie (dla [sekcji 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) na stronie 14) funkcje *xaxis*, *yaxis*, i *zaxis* mogą być wykonywane jednocześnie. Pierwszy `section` dyrektywa jest opcjonalne.  Należy pamiętać, że wszystkie `section` dyrektywy muszą występować w zakresie leksykalne `parallel sections` utworzenia.  
  
```  
#pragma omp parallel sections  
{  
    #pragma omp section  
        xaxis();  
    #pragma omp section  
        yaxis();  
    #pragma omp section  
        zaxis();  
}  
```
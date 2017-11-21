---
title: "A.8 określanie sekcji równoległych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d369c2e3a0d326ab4c835a30681f3dbe50f789f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
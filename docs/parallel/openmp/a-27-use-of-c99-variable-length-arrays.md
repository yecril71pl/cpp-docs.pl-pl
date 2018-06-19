---
title: Użycie A.27 tablice o zmiennej długości C99 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8e542701-39f9-4f28-ab3a-840e8e669723
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96391aa7403a54160cb6ab83b9b28c1527a3e353
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690094"
---
# <a name="a27---use-of-c99-variable-length-arrays"></a>A.27   Użycie tablic C99 o zmiennej długości
W poniższym przykładzie pokazano, jak używać C99 zmiennej długości tablic (VLAs) `firstprivate` — dyrektywa ([sekcji 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) na stronie 26).  
  
> [!NOTE]
>  Tablice o zmiennej długości nie są obecnie obsługiwane w programie Visual C++.  
  
```  
void f(int m, int C[m][m])  
{  
    double v1[m];  
    ...  
    #pragma omp parallel firstprivate(C, v1)  
    ...  
}  
```
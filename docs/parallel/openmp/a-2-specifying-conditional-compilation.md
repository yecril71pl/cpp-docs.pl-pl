---
title: Określanie kompilacja warunkowa A.2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d54245a2df2f38bed2674a3bb3923f8212d35459
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="a2---specifying-conditional-compilation"></a>A.2   Określanie kompilacji warunkowej
Poniższe przykłady przedstawiają użycie kompilacja warunkowa użycie makra OpenMP `_OPENMP` ([2.2 sekcji](../../parallel/openmp/2-2-conditional-compilation.md) na stronie 8). Z kompilacji OpenMP `_OPENMP` makro staje się zdefiniowane.  
  
```  
# ifdef _OPENMP   
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```  
  
 Zdefiniowany operator preprocesora umożliwia więcej niż jeden makra w jednej dyrektywy.  
  
```  
# if defined(_OPENMP) && defined(VERBOSE)  
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```
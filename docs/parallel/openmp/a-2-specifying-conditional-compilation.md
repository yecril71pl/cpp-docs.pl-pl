---
title: "Określanie kompilacja warunkowa A.2 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b0888a8bfc3d920ed3338b2ab6182c09cb75097a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
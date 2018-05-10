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
ms.openlocfilehash: b3d8c7073548c015d9982b721387176a0ca658c2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="22-conditional-compilation"></a>2.2 Kompilacja warunkowa
_**OPENMP** nazwy makra jest zdefiniowany przez implementacje zgodne OpenMP jako stałej dziesiętnej *yyyymm*, który będzie wybrany rok i miesiąc specyfikacji zatwierdzone. To makro nie może być przedmiotem **#define** lub **#undef** dyrektywy przetwarzania wstępnego.  
  
```  
#ifdef _OPENMP  
iam = omp_get_thread_num() + index;  
#endif  
```  
  
 Jeśli dostawców zdefiniowane rozszerzenia do OpenMP, ich może określić dodatkowe wstępnie zdefiniowane makra.
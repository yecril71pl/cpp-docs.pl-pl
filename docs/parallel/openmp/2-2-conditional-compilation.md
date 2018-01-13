---
title: 2.2 kompilacja warunkowa | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fb58458710c18f89f4057061b9c67b4eef1bbf0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="22-conditional-compilation"></a>2.2 Kompilacja warunkowa
_**OPENMP** nazwy makra jest zdefiniowany przez implementacje zgodne OpenMP jako stałej dziesiętnej *yyyymm*, który będzie wybrany rok i miesiąc specyfikacji zatwierdzone. To makro nie może być przedmiotem **#define** lub **#undef** dyrektywy przetwarzania wstępnego.  
  
```  
#ifdef _OPENMP  
iam = omp_get_thread_num() + index;  
#endif  
```  
  
 Jeśli dostawców zdefiniowane rozszerzenia do OpenMP, ich może określić dodatkowe wstępnie zdefiniowane makra.
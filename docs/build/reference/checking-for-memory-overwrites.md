---
title: "Sprawdzanie dla zastąpienia w pamięci | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4560fb580d3d1b24feccf84dc07bde7dc38458c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="checking-for-memory-overwrites"></a>Sprawdzanie nadpisywania pamięci
Jeśli na wywołanie funkcji manipulowania sterty naruszenia zasad dostępu, jest to możliwe, że program zawiera uszkodzone sterty. Typowym symptomem tej sytuacji mogą być następujące:  
  
```  
Access Violation in _searchseg  
```  
  
 [_Heapchk —](../../c-runtime-library/reference/heapchk.md) funkcja jest dostępna w obu debug i release kompiluje (tylko system Windows NT) do sprawdzania integralności sterty biblioteki czasu wykonywania. Można użyć `_heapchk` w znacznie taki sam sposób jak `AfxCheckMemory` funkcji, aby odizolować Zastąp sterty, na przykład:  
  
```  
if(_heapchk()!=_HEAPOK)  
   DebugBreak();  
```  
  
 Jeśli kiedykolwiek tej funkcji ulegnie awarii, należy do izolowania w takim przypadku stos został uszkodzony.  
  
## <a name="see-also"></a>Zobacz też  
 [Naprawianie problemów kompilacji wydania](../../build/reference/fixing-release-build-problems.md)
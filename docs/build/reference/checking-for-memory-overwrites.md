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
ms.workload: cplusplus
ms.openlocfilehash: 573710ae62384c8674009770b3c4fb29100db446
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
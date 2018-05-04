---
title: Sprawdzanie dla zastąpienia w pamięci | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 258aa6ae01d48df6717135f7dc8b73fc3f9e697a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
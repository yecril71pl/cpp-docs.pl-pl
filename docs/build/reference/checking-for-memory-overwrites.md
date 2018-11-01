---
title: Sprawdzanie nadpisywania pamięci
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: ff900c7366a28d19d3b90cbd4a6d9ee732e4ce02
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621562"
---
# <a name="checking-for-memory-overwrites"></a>Sprawdzanie nadpisywania pamięci

Jeśli naruszenie zasad dostępu na wywołanie funkcji manipulowania sterty, jest to możliwe, że program zawiera uszkodzone sterty. Typowym symptomem tej sytuacji mogą być następujące:

```
Access Violation in _searchseg
```

[_Heapchk —](../../c-runtime-library/reference/heapchk.md) funkcja jest dostępna w obu debug i release kompilacji (tylko Windows NT) w celu sprawdzenia integralności sterty biblioteki czasu wykonywania. Możesz użyć `_heapchk` w podobny sposób jak `AfxCheckMemory` funkcję, aby odizolować Zastąp sterty, na przykład:

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Jeśli ta funkcja nigdy nie zakończy się niepowodzeniem, należy do izolowania w tym momencie stos został uszkodzony.

## <a name="see-also"></a>Zobacz też

[Naprawianie problemów kompilacji wydania](../../build/reference/fixing-release-build-problems.md)
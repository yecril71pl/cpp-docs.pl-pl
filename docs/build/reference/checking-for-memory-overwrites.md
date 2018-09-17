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
ms.openlocfilehash: 246f625e899016080662f27a5901962c1c62f1a8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718653"
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
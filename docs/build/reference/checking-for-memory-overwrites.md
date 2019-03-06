---
title: Sprawdzanie nadpisywania pamięci
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: b37bd68519aea1194b601e89fefd0f14d428630a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422198"
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

## <a name="see-also"></a>Zobacz także

[Naprawianie problemów kompilacji wydania](../../build/reference/fixing-release-build-problems.md)

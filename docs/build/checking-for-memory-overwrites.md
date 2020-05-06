---
title: Sprawdzanie nadpisywania pamięci
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: 2c59cb96d640df6dcd96b9e0eafbcd325ed475f5
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342256"
---
# <a name="checking-for-memory-overwrites"></a>Sprawdzanie nadpisywania pamięci

W przypadku naruszenia zasad dostępu w wywołaniu funkcji operowania sterty istnieje możliwość, że program spowodował uszkodzenie sterty. Typowym objawem takiej sytuacji jest:

```
Access Violation in _searchseg
```

Funkcja [_heapchk](../c-runtime-library/reference/heapchk.md) jest dostępna zarówno w kompilacjach debugowania, jak i wydań (tylko system Windows NT) na potrzeby weryfikowania integralności sterty biblioteki czasu wykonywania. Można użyć `_heapchk` w ten sam sposób, co `AfxCheckMemory` funkcja do izolowania zastępowania sterty, na przykład:

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Jeśli ta funkcja kiedykolwiek się nie powiedzie, należy wyizolować, w którym momencie sterta została uszkodzona.

## <a name="see-also"></a>Zobacz też

[Naprawianie problemów kompilacji wydania](fixing-release-build-problems.md)

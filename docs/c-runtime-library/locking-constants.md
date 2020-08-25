---
title: _locking — Stałe
ms.date: 11/04/2016
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
helpviewer_keywords:
- LK_UNLCK constant
- LK_NBRLCK constant
- _LK_NBRLCK constant
- _LK_NBLCK constant
- _LK_LOCK constant
- LK_NBLCK constant
- _LK_UNLCK constant
- LK_RLCK constant
- _LK_RLCK constant
- LK_LOCK constant
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
ms.openlocfilehash: 8cfc1f933179e043f464a69f3ac5cf4ca25763e0
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830829"
---
# <a name="_locking-constants"></a>_locking — Stałe

## <a name="syntax"></a>Składnia

```
#include <sys/locking.h>
```

## <a name="remarks"></a>Uwagi

Argument *mode* w wywołaniu `_locking` funkcji określa akcję blokowania, która ma zostać wykonana.

Argument *mode* musi być jednym z następujących stałych manifestu.

|Wartość|Opis|
|-|-|
| `_LK_LOCK`  | Blokuje określone bajty. Jeśli bajty nie mogą być zablokowane, funkcja próbuje ponownie po 1 sekundzie. Jeśli po 10 próbach nie będzie można zablokować bajtów, funkcja zwróci błąd.  |
| `_LK_RLCK`  | Analogicznie jak `_LK_LOCK` .  |
|`_LK_NBLCK`  | Blokuje określone bajty. Jeśli bajty nie mogą być zablokowane, funkcja zwraca błąd.  |
| `_LK_NBRLCK`  | Analogicznie jak `_LK_NBLCK` .  |
| `_LK_UNLCK`  | Odblokowuje określone bajty. (Bajty muszą być wcześniej zablokowane).  |

## <a name="see-also"></a>Zobacz też

[_locking](../c-runtime-library/reference/locking.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)

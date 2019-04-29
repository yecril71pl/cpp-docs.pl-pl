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
ms.openlocfilehash: d559a68e8fede6e0b6dd40505a041b14da703681
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343085"
---
# <a name="locking-constants"></a>_locking — Stałe

## <a name="syntax"></a>Składnia

```
#include <sys/locking.h>
```

## <a name="remarks"></a>Uwagi

*Tryb* argumentu w wywołaniu `_locking` funkcja określa blokowania Akcja do wykonania.

*Tryb* argument musi być jedną z następujących stałych manifestu.

|||
|-|-|
| `_LK_LOCK`  | Blokuje określonych bajtów. Jeśli nie można zablokować bajtów, funkcja próbuje ponownie po 1 sekundę. Jeśli po 10 próbach bajtów nie może być zablokowany, funkcja zwraca błąd.  |
| `_LK_RLCK`  | Taki sam jak `_LK_LOCK`.  |
|`_LK_NBLCK`  | Blokuje określonych bajtów. Jeśli nie można zablokować bajtów, funkcja zwraca błąd.  |
| `_LK_NBRLCK`  | Taki sam jak `_LK_NBLCK`.  |
| `_LK_UNLCK`  | Odblokowuje określonych bajtów. (Bajtów musi mieć wcześniej zablokowane.)  |

## <a name="see-also"></a>Zobacz także

[_locking](../c-runtime-library/reference/locking.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)

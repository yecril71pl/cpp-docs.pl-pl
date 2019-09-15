---
title: HUGE_VAL, _HUGE
ms.date: 11/04/2016
api_name:
- _HUGE
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _HUGE
- HUGE_VAL
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
ms.openlocfilehash: 3a0469b7158e765b1b1c6f34cb01c0e90beb1401
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940268"
---
# <a name="huge_val-_huge"></a>HUGE_VAL, _HUGE

## <a name="syntax"></a>Składnia

```
#include <math.h>
```

## <a name="remarks"></a>Uwagi

`HUGE_VAL`jest największą reprezentacją podwójnej wartości. Ta wartość jest zwracana przez wiele funkcji matematycznych w czasie wykonywania w przypadku wystąpienia błędu. Dla niektórych funkcji —`HUGE_VAL` jest zwracany. `HUGE_VAL`jest zdefiniowany jako `_HUGE`, ale funkcje matematyczne w czasie wykonywania `HUGE_VAL`zwracają. Należy również użyć `HUGE_VAL` w kodzie, aby zapewnić spójność.

## <a name="see-also"></a>Zobacz także

[Stałe globalne](../c-runtime-library/global-constants.md)

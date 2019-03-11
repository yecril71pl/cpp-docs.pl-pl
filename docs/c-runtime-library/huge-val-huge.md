---
title: HUGE_VAL, _HUGE
ms.date: 11/04/2016
apiname:
- _HUGE
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _HUGE
- HUGE_VAL
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
ms.openlocfilehash: e6e3ec4c59ad22510233289d901fd3a89cb0d257
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743166"
---
# <a name="hugeval-huge"></a>HUGE_VAL, _HUGE

## <a name="syntax"></a>Składnia

```
#include <math.h>
```

## <a name="remarks"></a>Uwagi

`HUGE_VAL` jest największa wartość double. Ta wartość jest zwracana przez wiele funkcji matematycznych w czasie wykonywania, gdy wystąpi błąd. W przypadku niektórych funkcji-`HUGE_VAL` jest zwracana. `HUGE_VAL` jest zdefiniowany jako `_HUGE`, ale zwraca funkcje matematyczne środowiska wykonawczego `HUGE_VAL`. Należy również użyć `HUGE_VAL` w kodzie w celu zachowania spójności.

## <a name="see-also"></a>Zobacz także

[Stałe globalne](../c-runtime-library/global-constants.md)

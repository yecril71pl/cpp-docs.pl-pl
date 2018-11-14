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
ms.openlocfilehash: 8f8342990ea62b368b46ed56f0697a844c755a61
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522132"
---
# <a name="hugeval-huge"></a>HUGE_VAL, _HUGE

## <a name="syntax"></a>Składnia

```

#include <math.h>
```

## <a name="remarks"></a>Uwagi

`HUGE_VAL` jest największa wartość double. Ta wartość jest zwracana przez wiele funkcji matematycznych w czasie wykonywania, gdy wystąpi błąd. W przypadku niektórych funkcji-`HUGE_VAL` jest zwracana. `HUGE_VAL` jest zdefiniowany jako `_HUGE`, ale zwraca funkcje matematyczne środowiska wykonawczego `HUGE_VAL`. Należy również użyć `HUGE_VAL` w kodzie w celu zachowania spójności.

## <a name="see-also"></a>Zobacz też

[Stałe globalne](../c-runtime-library/global-constants.md)
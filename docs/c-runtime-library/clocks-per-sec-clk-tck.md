---
title: CLOCKS_PER_SEC, CLK_TCK
ms.date: 11/04/2016
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
ms.openlocfilehash: 40401028ef16f0d46baec92a37b2ba422d1e56ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621354"
---
# <a name="clockspersec-clktck"></a>CLOCKS_PER_SEC, CLK_TCK

## <a name="syntax"></a>Składnia

```

#include <time.h>
```

## <a name="remarks"></a>Uwagi

Czas w sekundach jest wartość zwrócona przez obiekt `clock` funkcji, podzielona przez `CLOCKS_PER_SEC`. `CLK_TCK` jest równoważny, ale uznany za przestarzały.

## <a name="see-also"></a>Zobacz też

[clock](../c-runtime-library/reference/clock.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
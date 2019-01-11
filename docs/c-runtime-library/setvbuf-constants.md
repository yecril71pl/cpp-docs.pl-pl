---
title: setvbuf — Stałe
ms.date: 11/04/2016
f1_keywords:
- _IOFBF
- _IONBF
- _IOLBF
helpviewer_keywords:
- _IOFBF constant
- IOFBF constant
- IONBF constant
- _IOLBF constant
- IOLBF constant
- _IONBF constant
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
ms.openlocfilehash: 8936789f4e3c9349e9d79616c8506c044dc79f70
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220403"
---
# <a name="setvbuf-constants"></a>setvbuf — Stałe

## <a name="syntax"></a>Składnia

```
#include <stdio.h>
```

## <a name="remarks"></a>Uwagi

Te stałe reprezentuje typ bufor w poszukiwaniu `setvbuf`.

Możliwe wartości są podane przy użyciu następujących stałych manifestu:

|Stała|Znaczenie|
|--------------|-------------|
|`_IOFBF`|Pełne buforowanie: Bufor określony w wywołaniu `setvbuf` jest używany, a jego rozmiar jest jako określone w `setvbuf` wywołania. Jeśli wskaźnik buforu jest **NULL**, automatycznie przydzielonego buforu określony rozmiar jest używany.|
|`_IOLBF`|Taki sam jak `_IOFBF`.|
|`_IONBF`|Bufor nie jest używany, niezależnie od argumentów w wywołaniu `setvbuf`.|

## <a name="see-also"></a>Zobacz też

[setbuf](../c-runtime-library/reference/setbuf.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)

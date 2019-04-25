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
ms.openlocfilehash: 28c9debf7e51d06cb9a625bb0a52d578ce3142c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268927"
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

## <a name="see-also"></a>Zobacz także

[setbuf](../c-runtime-library/reference/setbuf.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)

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
ms.openlocfilehash: 25c25741f54c1383a5bad9038b5b5d761dacdd89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458057"
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
|`_IOFBF`|Pełne buforowanie: bufor określony w wywołaniu `setvbuf` jest używana, a jego rozmiar jest jako określone w `setvbuf` wywołania. Jeśli wskaźnik buforu jest **NULL**, automatycznie przydzielonego buforu określony rozmiar jest używany.|
|`_IOLBF`|Taki sam jak `_IOFBF`.|
|`_IONBF`|Bufor nie jest używany, niezależnie od argumentów w wywołaniu `setvbuf`.|

## <a name="see-also"></a>Zobacz też

[setbuf](../c-runtime-library/reference/setbuf.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
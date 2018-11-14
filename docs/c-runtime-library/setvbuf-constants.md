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
ms.openlocfilehash: 661cf64c71e06c222503388df198d47429566602
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523809"
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
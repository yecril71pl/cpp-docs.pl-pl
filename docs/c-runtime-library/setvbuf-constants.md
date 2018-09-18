---
title: setvbuf — stałe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _IOFBF
- _IONBF
- _IOLBF
dev_langs:
- C++
helpviewer_keywords:
- _IOFBF constant
- IOFBF constant
- IONBF constant
- _IOLBF constant
- IOLBF constant
- _IONBF constant
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a367522c2f22007abcf24cdf74ada467d94b104
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032825"
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
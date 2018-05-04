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
ms.openlocfilehash: 0d4292ae29602b5890a167a3e2c29e460d65373f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="setvbuf-constants"></a>setvbuf — Stałe
## <a name="syntax"></a>Składnia  
  
```  
  
#include <stdio.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Te stałe odpowiada typowi buforu dla `setvbuf`.  
  
 Możliwe wartości są podane w następujących stałych manifestu:  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_IOFBF`|Pełne buforowanie: bufor określony w wywołaniu `setvbuf` jest używany, a jego rozmiar jest jako określone w `setvbuf` wywołania. Jeśli jest wskaźnika buforu **NULL**, automatycznie przydzielonego bufor określony rozmiar jest używany.|  
|`_IOLBF`|Taki sam jak `_IOFBF`.|  
|`_IONBF`|Bufor nie jest używane niezależnie od argumentów w wywołaniu `setvbuf`.|  
  
## <a name="see-also"></a>Zobacz też  
 [setbuf](../c-runtime-library/reference/setbuf.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)
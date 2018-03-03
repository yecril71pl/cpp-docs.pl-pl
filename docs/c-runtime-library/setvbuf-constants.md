---
title: "setvbuf — stałe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6bdb0fd3ad3811e756458090a963f78bd716a581
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
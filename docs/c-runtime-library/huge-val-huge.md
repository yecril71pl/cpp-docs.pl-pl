---
title: "HUGE_VAL —, _HUGE — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _HUGE
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _HUGE
- HUGE_VAL
dev_langs:
- C++
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27fbb0ae4f8bbe658c37c0e979ea97a4dcec2fb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hugeval-huge"></a>HUGE_VAL, _HUGE
## <a name="syntax"></a>Składnia  
  
```  
  
#include <math.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 `HUGE_VAL`jest reprezentacja największą wartość dwa razy. Ta wartość jest zwracana przez wiele funkcji matematycznych w czasie wykonywania, gdy wystąpi błąd. Do niektórych funkcji-`HUGE_VAL` jest zwracany. `HUGE_VAL`nie zdefiniowano jako `_HUGE`, ale zwraca funkcje matematyczne środowiska wykonawczego `HUGE_VAL`. Należy też używać `HUGE_VAL` w kodzie spójności.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe globalne](../c-runtime-library/global-constants.md)
---
title: HUGE_VAL —, _HUGE — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2d763b8c5379223ddacb8077c463efa0b91acfa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390508"
---
# <a name="hugeval-huge"></a>HUGE_VAL, _HUGE
## <a name="syntax"></a>Składnia  
  
```  
  
#include <math.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 `HUGE_VAL` jest reprezentacja największą wartość dwa razy. Ta wartość jest zwracana przez wiele funkcji matematycznych w czasie wykonywania, gdy wystąpi błąd. Do niektórych funkcji-`HUGE_VAL` jest zwracany. `HUGE_VAL` nie zdefiniowano jako `_HUGE`, ale zwraca funkcje matematyczne środowiska wykonawczego `HUGE_VAL`. Należy też używać `HUGE_VAL` w kodzie spójności.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe globalne](../c-runtime-library/global-constants.md)
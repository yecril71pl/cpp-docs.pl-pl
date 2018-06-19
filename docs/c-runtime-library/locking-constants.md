---
title: _locking — stałe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
dev_langs:
- C++
helpviewer_keywords:
- LK_UNLCK constant
- LK_NBRLCK constant
- _LK_NBRLCK constant
- _LK_NBLCK constant
- _LK_LOCK constant
- LK_NBLCK constant
- _LK_UNLCK constant
- LK_RLCK constant
- _LK_RLCK constant
- LK_LOCK constant
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 588c286cbad5e0097394a38eed34c09fc04af3ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389972"
---
# <a name="locking-constants"></a>_locking — Stałe
## <a name="syntax"></a>Składnia  
  
```  
  
#include <sys/locking.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 *Tryb* argument w wywołaniu `_locking` funkcja określa blokowania akcji do wykonania.  
  
 *Tryb* argument musi być jedną z następujących stałych manifestu.  
  
 `_LK_LOCK`  
 Umożliwia zablokowanie określonych bajtów. Jeśli bajtów nie może być zablokowany, funkcja próbuje ponownie po 1 sekundę. Jeśli po 10 próbach bajtów nie może być zablokowany, funkcja zwraca błąd.  
  
 `_LK_RLCK`  
 Taki sam jak `_LK_LOCK`.  
  
 `_LK_NBLCK`  
 Umożliwia zablokowanie określonych bajtów. Jeśli bajtów nie może być zablokowany, funkcja zwraca błąd.  
  
 `_LK_NBRLCK`  
 Taki sam jak `_LK_NBLCK`.  
  
 `_LK_UNLCK`  
 Umożliwia odblokowanie określonych bajtów. (Bajty musi mieć wcześniej zablokowane.)  
  
## <a name="see-also"></a>Zobacz też  
 [_locking —](../c-runtime-library/reference/locking.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)
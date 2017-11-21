---
title: "_locking — stałe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
dev_langs: C++
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
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 799b00209463c90c61b4b497a88af39ba554cd01
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
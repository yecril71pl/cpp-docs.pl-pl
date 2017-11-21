---
title: "_Rtc_numerrors — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _RTC_NumErrors
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _RTC_NumErrors
- RTC_NumErrors
dev_langs: C++
helpviewer_keywords:
- run-time errors
- _RTC_NumErrors function
- RTC_NumErrors function
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 62e734fb1165bf0d4e59f3d964a20056fa7065f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rtcnumerrors"></a>_RTC_NumErrors
Zwraca sumę błędów, które mogą być wykryte przez sprawdzanie błędów czasu wykonywania (RTC). Numer ten może posłużyć jako formant w **dla** pętli, w której każda wartość w pętli są przekazywane do [_rtc_geterrdesc —](../../c-runtime-library/reference/rtc-geterrdesc.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
int _RTC_NumErrors( void );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba całkowita, którego wartość reprezentuje całkowita liczba błędów, które mogą być wykryte przez sprawdzanie błędów czasu wykonywania Visual C++.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_RTC_NumErrors`|\<rtcapi.h >|  
  
 Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [_Rtc_geterrdesc —](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)
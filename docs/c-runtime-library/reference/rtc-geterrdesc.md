---
title: "_Rtc_geterrdesc — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _RTC_GetErrDesc
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
- RTC_GetErrDesc
- _RTC_GetErrDesc
dev_langs: C++
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 792407af9497148bea95333ee18028e0f8c953e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rtcgeterrdesc"></a>_RTC_GetErrDesc
Zwraca krótki opis typu (RTC) sprawdzanie błędów czasu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      const char * _RTC_GetErrDesc(  
   _RTC_ErrorNumber errnum   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *errnum*  
 Liczbą z zakresu od zera do jednego mniejsza niż wartość zwrócona przez `_RTC_NumErrors`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ciąg znaków, który zawiera krótki opis jednego z typów błędów wykrytych przez system sprawdzanie błędów czasu wykonywania. Jeśli błąd jest większa niż zero lub większa niż wartość zwrócona przez [_rtc_numerrors —](../../c-runtime-library/reference/rtc-numerrors.md), `_RTC_GetErrDesc` zwraca wartość NULL.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_RTC_GetErrDesc`|\<rtcapi.h >|  
  
 Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [_Rtc_numerrors —](../../c-runtime-library/reference/rtc-numerrors.md)   
 [Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)
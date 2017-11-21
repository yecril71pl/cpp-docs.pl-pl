---
title: "_Rtc_seterrortype — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _RTC_SetErrorType
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
- RTC_SetErrorType
- _RTC_SetErrorType
dev_langs: C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f695cb018a09725f23fb0943f9acbef83a338314
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rtcseterrortype"></a>_RTC_SetErrorType
Kojarzy błąd, który jest wykrywany przez sprawdzanie błędów czasu wykonywania (RTCs) z typem. Twoje obsługi błędu przetwarza jak dane wyjściowe błędów określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int _RTC_SetErrorType(  
   _RTC_ErrorNumber errnum,  
   int ErrType   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *errnum*  
 Liczbą z zakresu od zera do jednego mniejsza niż wartość zwrócona przez [_rtc_numerrors —](../../c-runtime-library/reference/rtc-numerrors.md).  
  
 *ErrType*  
 Wartość można przypisać do tego *errnum*. Na przykład może użyć **_CRT_ERROR**. Jeśli używasz `_CrtDbgReport` jako programu obsługi błędu *ErrType* może mieć tylko jedną symbole zdefiniowane w [_crtsetreportmode —](../../c-runtime-library/reference/crtsetreportmode.md). Jeśli masz własne program obsługi błędów ([_rtc_seterrorfunc —](../../c-runtime-library/reference/rtc-seterrorfunc.md)), może mieć tyle *ErrType*są określane jako miejsca *errnum*s.  
  
 *ErrType* _RTC_ERRTYPE_IGNORE ma specjalne znaczenie `_CrtSetReportMode`; ten błąd jest ignorowany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Poprzednia wartość dla typu błędu `type`.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie wszystkie błędy są ustawione na *ErrType* = 1, która odpowiada **_CRT_ERROR**. Aby uzyskać więcej informacji o błędzie domyślne typy takich jak **_CRT_ERROR**, zobacz [_crtdbgreport —](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).  
  
 Przed wywołaniem tej funkcji, należy najpierw wywołać jednej z funkcji inicjowania sprawdzanie błędów czasu wykonywania; zobacz [przy użyciu sprawdza czasu wykonywania bez biblioteki wykonawczej języka C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_RTC_SetErrorType`|\<rtcapi.h >|  
  
 Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [_Rtc_geterrdesc —](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)
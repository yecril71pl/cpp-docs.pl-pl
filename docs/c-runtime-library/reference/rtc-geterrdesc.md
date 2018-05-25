---
title: _Rtc_geterrdesc — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _RTC_GetErrDesc
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
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7154f6de192ee6b681ed0419126f3d4b682abb8c
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="rtcgeterrdesc"></a>_RTC_GetErrDesc

Zwraca krótki opis typu (RTC) sprawdzanie błędów czasu wykonywania.

## <a name="syntax"></a>Składnia

```C
const char * _RTC_GetErrDesc(
   _RTC_ErrorNumber errnum
);
```

### <a name="parameters"></a>Parametry

*errnum*<br/>
Liczbą z zakresu od zera do jednego mniejsza niż wartość zwrócona przez **_rtc_numerrors —**.

## <a name="return-value"></a>Wartość zwracana

Ciąg znaków, który zawiera krótki opis jednego z typów błędów wykrytych przez system sprawdzanie błędów czasu wykonywania. Jeśli błąd jest większa niż zero lub większa niż wartość zwrócona przez [_rtc_numerrors —](rtc-numerrors.md), **_rtc_geterrdesc —** zwraca **NULL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_RTC_GetErrDesc**|\<rtcapi.h>|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[_RTC_NumErrors](rtc-numerrors.md)<br/>
[Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)<br/>

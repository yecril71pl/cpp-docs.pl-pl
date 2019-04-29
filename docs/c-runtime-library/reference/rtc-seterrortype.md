---
title: _RTC_SetErrorType
ms.date: 11/04/2016
apiname:
- _RTC_SetErrorType
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
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
ms.openlocfilehash: 022079bd199477c8bca92e853ed66879c96428db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357138"
---
# <a name="rtcseterrortype"></a>_RTC_SetErrorType

Kojarzy błąd, który zostanie wykryty przez sprawdzanie błędów czasu wykonywania (RTCs) z typem. Twoja procedura obsługi błędów przetwarza jak produkt wyjściowy błędy określonego typu.

## <a name="syntax"></a>Składnia

```C
int _RTC_SetErrorType(
   _RTC_ErrorNumber errnum,
   int ErrType
);
```

### <a name="parameters"></a>Parametry

*errnum*<br/>
Liczbą z zakresu od zera i jeden mniejsza niż wartość zwrócona przez obiekt [_rtc_numerrors —](rtc-numerrors.md).

*ErrType*<br/>
Wartość do przypisania do tego *errnum*. Na przykład, można na przykład **_CRT_ERROR**. Jeśli używasz **_CrtDbgReport** jako procedurę obsługi błędów, *ErrType* może zawierać tylko jeden z symboli zdefiniowanych w [_CrtSetReportMode](crtsetreportmode.md). Jeśli masz własną procedurę obsługi błędów ([_RTC_SetErrorFunc](rtc-seterrorfunc.md)), może mieć tyle *ErrType*są określane jako miejsca *errnum*s.

*ErrType* _RTC_ERRTYPE_IGNORE ma specjalne znaczenie **_CrtSetReportMode**; błąd jest ignorowany.

## <a name="return-value"></a>Wartość zwracana

Poprzednią wartość dla typu błędu *typu*.

## <a name="remarks"></a>Uwagi

Domyślnie wszystkie błędy są ustawione na *ErrType* = 1, co odpowiada **_CRT_ERROR**. Aby uzyskać więcej informacji o błędzie domyślne typy takie jak **_CRT_ERROR**, zobacz [_CrtDbgReport](crtdbgreport-crtdbgreportw.md).

Przed wywołaniem tej funkcji, należy najpierw wywołać jedną z funkcji inicjowania sprawdzanie błędów czasu wykonywania; zobacz [przy użyciu kontroli czasu wykonywania bez biblioteki wykonawczej języka C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_RTC_SetErrorType**|\<rtcapi.h>|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)<br/>

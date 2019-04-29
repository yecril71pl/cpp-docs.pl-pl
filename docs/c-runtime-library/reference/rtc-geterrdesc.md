---
title: _RTC_GetErrDesc
ms.date: 11/04/2016
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
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
ms.openlocfilehash: d164626ea89bbe10f5b2ffe4224bf6381e40bab0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357385"
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
Liczbą z zakresu od zera i jeden mniejsza niż wartość zwrócona przez obiekt **_rtc_numerrors —**.

## <a name="return-value"></a>Wartość zwracana

Ciąg znaków, który zawiera krótki opis jednego z typów błędów, wykrytych przez system sprawdzanie błędów czasu wykonywania. Jeśli błąd jest mniejsza zero lub większa niż lub równa wartości zwracanej przez [_rtc_numerrors —](rtc-numerrors.md), **_RTC_GetErrDesc** zwraca **NULL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_RTC_GetErrDesc**|\<rtcapi.h>|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[_RTC_NumErrors](rtc-numerrors.md)<br/>
[Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)<br/>

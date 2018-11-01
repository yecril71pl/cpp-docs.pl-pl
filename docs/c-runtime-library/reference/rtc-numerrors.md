---
title: _RTC_NumErrors
ms.date: 11/04/2016
apiname:
- _RTC_NumErrors
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
helpviewer_keywords:
- run-time errors
- _RTC_NumErrors function
- RTC_NumErrors function
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
ms.openlocfilehash: e13f85f2140473d6e971d27abb6012effd36c37c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477197"
---
# <a name="rtcnumerrors"></a>_RTC_NumErrors

Zwraca całkowitą liczbę błędów, które mogą być wykryte przez sprawdzanie błędów czasu wykonywania (RTC). Numer ten może posłużyć jako formant w **dla** pętli, w którym każda wartość w pętli jest przekazywany do [_RTC_GetErrDesc](rtc-geterrdesc.md).

## <a name="syntax"></a>Składnia

```C

int _RTC_NumErrors( void );

```

## <a name="return-value"></a>Wartość zwracana

Liczba całkowita, których wartość reprezentuje całkowita liczba błędów, które mogą być wykryte przez sprawdzanie błędów czasu wykonywania Visual C++.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_RTC_NumErrors**|\<rtcapi.h>|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)<br/>

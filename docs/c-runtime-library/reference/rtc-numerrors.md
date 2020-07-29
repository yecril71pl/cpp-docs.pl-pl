---
title: _RTC_NumErrors
ms.date: 11/04/2016
api_name:
- _RTC_NumErrors
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _RTC_NumErrors
- RTC_NumErrors
helpviewer_keywords:
- run-time errors
- _RTC_NumErrors function
- RTC_NumErrors function
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
ms.openlocfilehash: 0e0af8596dbc7f48bc3f6b996219ec7c7a57749d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234032"
---
# <a name="_rtc_numerrors"></a>_RTC_NumErrors

Zwraca łączną liczbę błędów, które mogą zostać wykryte przez sprawdzanie błędów czasu wykonywania (RTC). Tej liczby można użyć jako formantu w **`for`** pętli, gdzie każda wartość w pętli jest przenoszona do [_RTC_GetErrDesc](rtc-geterrdesc.md).

## <a name="syntax"></a>Składnia

```C

int _RTC_NumErrors( void );
```

## <a name="return-value"></a>Wartość zwracana

Liczba całkowita, której wartość reprezentuje całkowitą liczbę błędów, które mogą zostać wykryte przez Visual C++ sprawdzenia błędów czasu wykonywania.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_RTC_NumErrors**|\<rtcapi.h>|

Aby uzyskać więcej informacji, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)<br/>

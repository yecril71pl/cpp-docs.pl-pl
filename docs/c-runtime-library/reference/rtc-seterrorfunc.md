---
title: _RTC_SetErrorFunc
ms.date: 11/04/2016
apiname:
- _RTC_SetErrorFunc
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
- RTC_SetErrorFunc
- _RTC_SetErrorFunc
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
ms.openlocfilehash: 6b292d685eea8eccb9e9b2a3c3e6cd903d501005
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514741"
---
# <a name="rtcseterrorfunc"></a>_RTC_SetErrorFunc

Określa funkcję jako program obsługi raportowania sprawdzanie błędów czasu wykonywania (RTCs). Ta funkcja jest przestarzała; Użyj **_RTC_SetErrorFuncW** zamiast tego.

## <a name="syntax"></a>Składnia

```C
_RTC_error_fn _RTC_SetErrorFunc(
   _RTC_error_fn function
);
```

### <a name="parameters"></a>Parametry

*— Funkcja*<br/>
Adres funkcji, która będzie obsługiwać sprawdzanie błędów czasu wykonywania.

## <a name="return-value"></a>Wartość zwracana

Funkcję wcześniej zdefiniowaną błędu. Jeśli nie ma zdefiniowanej wcześniej funkcji, zwraca **NULL**.

## <a name="remarks"></a>Uwagi

Nie należy używać tej funkcji; Zamiast tego należy użyć **_RTC_SetErrorFuncW**. Zachowywane tylko w przypadku zgodności z poprzednimi wersjami.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_RTC_SetErrorFunc**|\<rtcapi.h>|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)<br/>

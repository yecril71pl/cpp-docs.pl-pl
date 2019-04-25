---
title: _get_dstbias
ms.date: 11/04/2016
apiname:
- _get_dstbias
- __dstbias
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __dstbias
- _get_dstbias
- get_dstbias
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
ms.openlocfilehash: 61807f854dc9c2f7de6f0acd5bbf4668987ce49e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332380"
---
# <a name="getdstbias"></a>_get_dstbias

Pobiera przesunięcie czasu letniego w ciągu kilku sekund.

## <a name="syntax"></a>Składnia

```C
error_t _get_dstbias( int* seconds );
```

### <a name="parameters"></a>Parametry

*seconds*<br/>
Przesunięcie w ciągu kilku sekund czasu letniego.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli kończy się pomyślnie lub **errno** wartość, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

**_Get_dstbias —** funkcja pobiera liczbę sekund czasu letniego jako liczba całkowita. Jeśli zmiany czasu jest włączone, przesunięcie domyślne wynosi 3600 sekund, czyli liczbę sekund w ciągu jednej godziny (chociaż kilku regionach obserwować przesunięcie dwóch godzin).

Jeśli *sekund* jest **NULL**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **EINVAL**.

Firma Microsoft zaleca, aby użyć tej funkcji zamiast makro **_dstbias** lub zaniechanej funkcji **__dstbias**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_dstbias**|\<time.h>|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>

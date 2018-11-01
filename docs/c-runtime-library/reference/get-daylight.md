---
title: _get_daylight
ms.date: 11/04/2016
apiname:
- __daylight
- _get_daylight
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
- get_daylight
- _get_daylight
helpviewer_keywords:
- get_daylight function
- daylight saving time offset
- _get_daylight function
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
ms.openlocfilehash: 03c3386e59379f460d3c07dc310153d990c02b05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444645"
---
# <a name="getdaylight"></a>_get_daylight

Pobiera przesunięcie czasu w godzinach.

## <a name="syntax"></a>Składnia

```C
error_t _get_daylight( int* hours );
```

### <a name="parameters"></a>Parametry

*godz.*<br/>
Przesunięcie w godzinach okresu obowiązywania czasu letniego.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli kończy się pomyślnie lub **errno** wartość, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

**_Get_daylight —** funkcja pobiera liczbę godzin w czasu letniego jako liczba całkowita. Jeśli obowiązuje czas letni, przesunięcie domyślny to jedna godzina (chociaż kilku regionach obserwować przesunięcie dwóch godzin).

Jeśli *godzin* jest **NULL**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **EINVAL**.

Firma Microsoft zaleca, aby użyć tej funkcji zamiast makro **_daylight** lub zaniechanej funkcji **__daylight**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_daylight**|\<time.h>|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>

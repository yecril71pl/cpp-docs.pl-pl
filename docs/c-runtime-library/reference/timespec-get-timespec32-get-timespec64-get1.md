---
title: timespec_get, _timespec32_get, _timespec64_get1
ms.date: 11/04/2016
api_name:
- timespec_get
- _timespec32_get
- _timespec64_get
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
- api-ms-win-crt-time-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- timespec_get
- _timespec32_get
- _timespec64_get
- time/timespec_get
- time/_timespec32_get
- time/_timespec64_get
- timespec
- _timespec32
- _timespec64
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
ms.openlocfilehash: c0517c974bf58d502133ccd9868149bd178790d6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957618"
---
# <a name="timespec_get-_timespec32_get-_timespec64_get"></a>timespec_get, _timespec32_get, _timespec64_get

Ustawia interwał wskazywany przez pierwszy argument do bieżącego czasu kalendarza w oparciu o określony czas podstawowy.

## <a name="syntax"></a>Składnia

```C
int timespec_get(
    struct timespec* const time_spec,
    int const base
);
int _timespec32_get(
    struct _timespec32* const time_spec,
    int const base
);
int _timespec64_get(
    struct _timespec64* const time_spec,
    int const base
);
```

### <a name="parameters"></a>Parametry

*time_spec*<br/>
Wskaźnik do struktury, która jest ustawiona na czas w sekundach i nanosekundach od momentu rozpoczęcia epoki.

*base*<br/>
Różna od zera wartość specyficzna dla implementacji, która określa podstawę czasu.

## <a name="return-value"></a>Wartość zwracana

Wartość *podstawowa* , jeśli się powiedzie, w przeciwnym razie zwraca wartość zero.

## <a name="remarks"></a>Uwagi

Funkcje **timespec_get** ustawiają bieżący czas w strukturze wskazywany przez argument *time_spec* . Wszystkie wersje tej struktury mają dwa elementy członkowskie, **tv_sec** i **tv_nsec**. Wartość **tv_sec** jest ustawiona na całkowitą liczbę sekund i **tv_nsec** na całkowitą liczbę nanosekund, zaokrągloną do rozdzielczości zegara systemowego, od momentu rozpoczęcia epoki określonej przez *podstawę*.

**Microsoft Specific**

Te funkcje obsługują tylko **TIME_UTC** jako wartość *bazową* . Ustawia wartość *time_spec* na liczbę sekund i nanosekund od momentu rozpoczęcia epoki, północy, 1 stycznia 1970, uniwersalny czas koordynowany (UTC). W **strukturze** **_timespec32** **tv_sec** jest wartością **__time32_t** . W **strukturze** **_timespec64** **tv_sec** jest wartością **__time64_t** . W **strukturze** **timespec** **tv_sec** jest typem **time_t** , który jest 32 bity lub 64 bitów w zależności od tego, czy zdefiniowano _USE_32BIT_TIME_T makro preprocesora. Funkcja **timespec_get** jest wbudowaną funkcją, która wywołuje **_TIMESPEC32_GET** , jeśli _USE_32BIT_TIME_T jest zdefiniowany; w przeciwnym razie wywołuje **_timespec64_get**.

**Zakończenie określonych przez firmę Microsoft**

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**timespec_get**, **_timespec32_get**, **_timespec64_get**|C: \<Time. h >, C++: \<CTime > lub \<Time. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>

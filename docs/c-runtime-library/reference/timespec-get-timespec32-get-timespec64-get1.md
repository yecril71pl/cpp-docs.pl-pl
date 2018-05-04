---
title: timespec_get, _timespec32_get, _timespec64_get1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- timespec_get
- _timespec32_get
- _timespec64_get
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
- timespec_get
- _timespec32_get
- _timespec64_get
- time/timespec_get
- time/_timespec32_get
- time/_timespec64_get
- timespec
- _timespec32
- _timespec64
dev_langs:
- C++
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f00a59f8b5813398b47562b106f3ec0eff3363b1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="timespecget-timespec32get-timespec64get"></a>timespec_get, _timespec32_get, _timespec64_get

Ustawia interwał wskazywana przez pierwszy argument bieżący czas kalendarza na podstawie określonego czasu podstawowej.

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
Wskaźnik do struktury ustawionej na czas w sekundach i nanosekundach, od chwili uruchomienia epoka.

*base*<br/>
Wartość konkretnej implementacji inną niż zero, która określa podstawowy czas.

## <a name="return-value"></a>Wartość zwracana

Wartość *podstawowej* przypadku powiodło się, w przeciwnym razie zwraca wartość zero.

## <a name="remarks"></a>Uwagi

**Timespec_get** funkcje ustawiać bieżący czas w strukturze wskazywana przez *time_spec* argumentu. Wszystkie wersje tej struktury mają dwa elementy członkowskie, **tv_sec** i **tv_nsec**. **Tv_sec** ma wartość całkowitą liczbę sekund i **tv_nsec** z całkowitą liczbą nanosekundach zaokrąglona do rozdzielczość zegara systemowego od chwili uruchomienia epoki określony przez *podstawowej*.

**Microsoft Specific**

Te funkcje obsługuje tylko **TIME_UTC** jako *podstawowej* wartość. To ustawienie *time_spec* wartość liczby sekund i nanosekundach, od momentu uruchomienia epoka północy, 1 stycznia 1970 r. uniwersalnego czasu koordynowanego (UTC). W **struktury** **_timespec32**, **tv_sec** jest **__time32_t** wartości. W **struktury** **_timespec64**, **tv_sec** jest **__time64_t —** wartość. W **struktury** **timespec**, **tv_sec** jest **time_t —** typu, który jest 32-bitowy lub 64-bitowy długości w zależności od tego, czy preprocesora Makro _USE_32BIT_TIME_T jest zdefiniowany. **Timespec_get** funkcji jest wbudowaną funkcją wywołującą **_timespec32_get** Jeśli zdefiniowano _USE_32BIT_TIME_T; w przeciwnym razie wywołuje **_timespec64_get**.

**Końcowy określonych firmy Microsoft**

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**timespec_get**, **_timespec32_get**, **_timespec64_get**|C: \<time.h >, C++: \<ctime — > lub \<time.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

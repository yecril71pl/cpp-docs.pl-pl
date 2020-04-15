---
title: _mkgmtime, _mkgmtime32, _mkgmtime64
description: W tym artykule opisano funkcje biblioteki _mkgmtime, _mkgmtime32 i _mkgmtime64 C runtime i podano przykłady sposobu ich używania.
ms.date: 4/2/2020
api_name:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
- _o__mkgmtime32
- _o__mkgmtime64
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
ms.openlocfilehash: e8b3170fc0413a878777035fd76aac5eefa7b6bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338772"
---
# <a name="_mkgmtime-_mkgmtime32-_mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64

Konwertuje czas UTC reprezentowany przez **tm struktury** **tm** czas UTC reprezentowane przez **typ time_t.**

## <a name="syntax"></a>Składnia

```C
time_t _mkgmtime(
   struct tm* timeptr
);
__time32_t _mkgmtime32(
   struct tm* timeptr
);
__time64_t _mkgmtime64(
   struct tm* timeptr
);
```

### <a name="parameters"></a>Parametry

*timeptr*\
Wskaźnik do czasu UTC jako **tm** **struktury** do konwersji.

## <a name="return-value"></a>Wartość zwracana

Ilość typu **__time32_t** lub **__time64_t** reprezentująca liczbę sekund, które upłynęło od północy, 1 stycznia 1970 r., w skoordynowanym czasie uniwersalnym (UTC). Jeśli data jest poza zakresem (patrz uwaga sekcji) lub dane wejściowe nie mogą być interpretowane jako prawidłowy czas, zwracana wartość wynosi -1.

## <a name="remarks"></a>Uwagi

Funkcje **_mkgmtime32** i **_mkgmtime64** konwertuje czas UTC na **typ __time32_t** lub **__time64_t** reprezentujący czas w czasie utc. Aby przekonwertować czas lokalny na czas UTC, użyj **mktime**, **_mktime32**i **zamiast tego _mktime64.**

**_mkgmtime** jest funkcją wbudowaną, która ocenia **_mkgmtime64,** a **time_t** jest odpowiednikiem **__time64_t**. Jeśli konieczne jest wymuszenie, aby kompilator interpretował **time_t** jako stary **time_t**32-bitowy, można zdefiniować **_USE_32BIT_TIME_T**. Nie zalecamy, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 r., maksymalny zakres 32-bitowej **time_t**. Nie jest to dozwolone w ogóle na platformach 64-bitowych.

Przeniesiona struktura czasu jest zmieniana w następujący sposób, w taki sam sposób, jak jest zmieniana przez funkcje **_mktime:** pola **tm_wday** i **tm_yday** są ustawione na nowe wartości na podstawie wartości **tm_mday** i **tm_year**. Ponieważ zakłada się, że czas jest UTC, **pole tm_isdst** jest ignorowane.

Zakres funkcji **_mkgmtime32** wynosi od północy, 1 stycznia 1970, UTC do 23:59:59 18 stycznia 2038, UTC. Zakres **_mkgmtime64** wynosi od północy, 1 stycznia 1970, UTC do 23:59:59, 31 grudnia 3000, UTC. Data poza zakresem powoduje wartość zwracaną -1. Zakres **_mkgmtime** zależy od tego, czy **_USE_32BIT_TIME_T** jest zdefiniowany. Jeśli nie jest zdefiniowany, co jest ustawieniem domyślnym, zakres jest taki sam jak **_mkgmtime64**. W przeciwnym razie zakres jest ograniczony do 32-bitowego zakresu **_mkgmtime32**.

Zarówno **gmtime,** jak i **localtime** używają wspólnego bufora statycznego do konwersji. Jeśli ten bufor zostanie **_mkgmtime,** poprzednia zawartość zostanie zniszczona.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="examples"></a>Przykłady

```C
// crt_mkgmtime.c
#include <stdio.h>
#include <time.h>

int main()
{
    struct tm t1, t2;
    time_t now, mytime, gmtime;
    char buff[30];

    time( & now );

    _localtime64_s( &t1, &now );
    _gmtime64_s( &t2, &now );

    mytime = mktime(&t1);
    gmtime = _mkgmtime(&t2);

    printf("Seconds since midnight, January 1, 1970\n");
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);

    /* Use asctime_s to display these times. */

    _localtime64_s( &t1, &mytime );
    asctime_s( buff, sizeof(buff), &t1 );
    printf( "Local Time: %s\n", buff );

    _gmtime64_s( &t2, &gmtime );
    asctime_s( buff, sizeof(buff), &t2 );
    printf( "Greenwich Mean Time: %s\n", buff );

}
```

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

W poniższym przykładzie pokazano, jak niekompletna struktura jest wypełniana przez **_mkgmtime**. Oblicza wartości zarówno dla dnia tygodnia, jak i roku.

```C
// crt_mkgmtime2.c
#include <stdio.h>
#include <time.h>
#include <memory.h>

int main()
{
    struct tm t1, t2;
    time_t gmtime;
    char buff[30];

    memset(&t1, 0, sizeof(struct tm));
    memset(&t2, 0, sizeof(struct tm));

    t1.tm_mon = 1;
    t1.tm_isdst = 0;
    t1.tm_year = 103;
    t1.tm_mday = 12;

    // The day of the week and year will be incorrect in the output here.
    asctime_s( buff, sizeof(buff), &t1);
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

    gmtime = _mkgmtime(&t1);

    // The correct day of the week and year were determined.
    asctime_s( buff, sizeof(buff), &t1);
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

}
```

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)\
[asctime, _wasctime](asctime-wasctime.md)\
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)\
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)\
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[time, _time32, _time64](time-time32-time64.md)

---
title: _mkgmtime, _mkgmtime32, _mkgmtime64
ms.date: 11/04/2016
api_name:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
ms.openlocfilehash: fcd1e3fdcca37d7e5bb381c234a6d8555ce2766c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951668"
---
# <a name="_mkgmtime-_mkgmtime32-_mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64

Konwertuje czas UTC reprezentowany przez **strukturę** **TM** do czasu UTC reprezentowanego przez typ **time_t** .

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

*timeptr*<br/>
Wskaźnik do czasu UTC jako **strukturę** **TM** do przekonwertowania.

## <a name="return-value"></a>Wartość zwracana

Ilość typu **__time32_t** lub **__time64_t** reprezentująca liczbę sekund, które upłynęły od północy, 1 stycznia 1970, w uniwersalnym czasie koordynowanym (UTC). Jeśli data jest poza zakresem (patrz sekcja uwagi) lub dane wejściowe nie mogą być interpretowane jako prawidłowy czas, wartość zwracana to-1.

## <a name="remarks"></a>Uwagi

Funkcje **_mkgmtime32** i **_mkgmtime64** konwertują czas UTC na typ **__time32_t** lub **__time64_t** reprezentujący godzinę w formacie UTC. Aby skonwertować czas lokalny na czas UTC, zamiast tego należy użyć **mktime**, **_mktime32**i **_mktime64** .

**_mkgmtime** jest funkcją wbudowaną, która jest obliczana do **_mkgmtime64**, a **time_t** jest równoznaczna z **__time64_t**. Jeśli trzeba wymusić, aby kompilator interpretował **time_t** jako stary 32-bitowy **time_t**, można zdefiniować **_USE_32BIT_TIME_T**. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 (maksymalnym zakresie 32-bitowym **time_t**) i nie jest to dozwolone na wszystkich platformach 64-bitowych.

Przeniesiona struktura czasu zostanie zmieniona w taki sam sposób, jak w przypadku ich zmiany za pomocą funkcji **_mktime** : pola **tm_wday** i **tm_yday** są ustawiane na nowe wartości na podstawie wartości **tm_mday** i **tm_year**. Podczas określania czasu struktury **TM** ustaw wartość pola **tm_isdst** na:

- Zero (0), aby wskazać, że obowiązuje czas standardowy.

- Wartość większa od 0 wskazuje, że obowiązuje czas letni.

- Wartość mniejsza od zera, aby można było obliczyć kod biblioteki wykonawczej C, niezależnie od tego, czy obowiązuje czas standardowy czy czas letni.

Biblioteka środowiska uruchomieniowego C używa zmiennej środowiskowej $ do określenia prawidłowego czasu letniego. Jeśli wartość opcji nie jest ustawiona, system operacyjny jest pytany w celu uzyskania prawidłowego zachowania w regionie czasu letniego. **tm_isdst** jest polem wymaganym. Jeśli nie zostanie ustawiona, jego wartość jest niezdefiniowana i wartość zwracana z **mktime** jest nieprzewidywalne.

Zakres funkcji **_mkgmtime32** jest z północy, 1 stycznia 1970, UTC do 23:59:59 stycznia 18, 2038, UTC. Zakres **_mkgmtime64** to od północy, 1 stycznia 1970, utc do 23:59:59, 31 grudnia 3000, UTC. Data poza zakresem daje wartość zwracaną-1. Zakres **_mkgmtime** zależy od tego, czy **_USE_32BIT_TIME_T** jest zdefiniowany. Jeśli nie jest zdefiniowany (wartość domyślna), zakresem jest **_mkgmtime64**; w przeciwnym razie zakres jest ograniczony do 32-bitowego zakresu **_mkgmtime32**.

Należy zauważyć, że **gmtime** i **localtime** używają jednego bufora przydzielenia statycznie dla konwersji. Jeśli podasz ten bufor do **mkgmtime**, poprzednia zawartość zostaje zniszczona.

## <a name="example"></a>Przykład

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

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

W poniższym przykładzie pokazano, jak Niekompletna struktura jest wypełniana wartościami obliczanymi dnia tygodnia i dniem roku.

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

### <a name="output"></a>Dane wyjściowe

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>

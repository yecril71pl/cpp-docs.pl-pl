---
title: gmtime_s, _gmtime32_s, _gmtime64_s
ms.date: 11/04/2016
apiname:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
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
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
helpviewer_keywords:
- gmtime_s function
- gmtime32_s function
- time functions
- gmtime64_s function
- _gmtime64_s function
- time structure conversion
- _gmtime_s function
- _gmtime32_s function
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
ms.openlocfilehash: 8225fed21ca9dc67440a4af5dcf43b2ad5cfdffb
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332468"
---
# <a name="gmtimes-gmtime32s-gmtime64s"></a>gmtime_s, _gmtime32_s, _gmtime64_s

Konwertuje wartość czasu **tm** struktury. Są to wersje [_gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t gmtime_s(
   struct tm* tmDest,
   const __time_t* sourceTime
);
errno_t _gmtime32_s(
   struct tm* tmDest,
   const __time32_t* sourceTime
);
errno_t _gmtime64_s(
   struct tm* tmDest,
   const __time64_t* sourceTime
);
```

### <a name="parameters"></a>Parametry

*tmDest*<br/>
Wskaźnik do [tm](../../c-runtime-library/standard-types.md) struktury. Pola zwróconej struktury przechowują ocenianą wartość z *czasomierza* argument w formacie UTC, a nie według czasu lokalnego.

*sourceTime*<br/>
Wskaźnik na czas przechowywania. Czas jest reprezentowany jako sekundach, które upłynęły od północy (00: 00:00), 1 stycznia 1970 r., skoordynowanego czasu uniwersalnego (UTC).

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie. Wartość zwracana jest kod błędu, jeśli wystąpi awaria. Kody błędów są zdefiniowane w Errno.h; Aby uzyskać listę tych błędów, zobacz [errno](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Warunki błędów

|*tmDest*|*sourceTime*|Wróć|Wartość w *tmDest*|
|-----------|------------|------------|--------------------|
|**NULL**|Wszystkie|**EINVAL**|Nie jest modyfikowany.|
|Nie **NULL** (wskazuje prawidłowy pamięci)|**NULL**|**EINVAL**|Wszystkie pola ustawione na wartość -1.|
|Nie **o wartości NULL**|< 0|**EINVAL**|Wszystkie pola ustawione na wartość -1.|

W przypadku pierwszego warunków błędów dwóch, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają **EINVAL**.

## <a name="remarks"></a>Uwagi

**_Gmtime32_s —** funkcja dzieli *sourceTime* wartości i zapisuje je w strukturze typu **tm**, zdefiniowanego w czasie.h. Adres struktury jest przekazywany w *tmDest*. Wartość *sourceTime* są zazwyczaj uzyskiwane z wywołania [czasu](time-time32-time64.md) funkcji.

> [!NOTE]
> Środowisko docelowe starać się ustalić, czy czas letni obowiązuje. Biblioteki wykonawczej C zakłada zasady Stanów Zjednoczonych wykonywania obliczeń czasu letniego.

Każde z pól struktury jest typu **int**, jak pokazano w poniższej tabeli.

|Pole|Opis|
|-|-|
|**tm_sec**|Sekundy po minucie (0 - 59).|
|**tm_min**|Min. po godzinie (0 - 59).|
|**tm_hour**|Godziny od północy (0 - 23).|
|**tm_mday**|Dzień miesiąca (1-31).|
|**tm_mon**|Miesiąc (0 - 11; Styczeń = 0).|
|**tm_year**|Rok (bieżący roku minus 1900).|
|**tm_wday**|Dzień tygodnia (0 – 6; Niedziela = 0).|
|**tm_yday**|Dzień roku (0 – 365; Od 1 stycznia = 0).|
|**tm_isdst**|Zawsze 0 dla **gmtime_s —**.|

**_gmtime64_s —**, który używa **__time64_t —** struktury, umożliwia daty do za pośrednictwem 23:59:59, 31 grudnia 3000, UTC, podczas gdy **gmtime32_s —** przedstawia tylko daty do 23:59:59 18 stycznia 2038 r. UTC. Północy 1 stycznia 1970 r., to dolna granica zakresu dat dla obu tych funkcji.

**gmtime_s —** jest funkcją śródwierszową, co jest ewaluowane jako **_gmtime64_s —** i **time_t** jest odpowiednikiem **__time64_t —**. Jeśli chcesz wymusić na kompilatorze interpretowanie **time_t** jako stary 32-bitowy **time_t**, można zdefiniować **_USE_32BIT_TIME_T**. Takie działanie spowoduje **gmtime_s —** być wyrównane z **_gmtime32_s —**. Nie jest to zalecane, ponieważ aplikacja może przestać działać po 18 stycznia 2038 r. i nie jest dozwolone na platformach 64-bitowych.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek języka C|Wymagany nagłówek C++|
|-------------|---------------------|-|
|**gmtime_s —**, **_gmtime32_s —**, **_gmtime64_s —**|\<time.h>|\<ctime — > lub \<time.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_gmtime64_s.c
// This program uses _gmtime64_s to convert a 64-bit
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime_s to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm newtime;
   __int64 ltime;
   char buf[26];
   errno_t err;

   _time64( &ltime );

   // Obtain coordinated universal time:
   err = _gmtime64_s( &newtime, &ltime );
   if (err)
   {
      printf("Invalid Argument to _gmtime64_s.");
   }

   // Convert to an ASCII representation
   err = asctime_s(buf, 26, &newtime);
   if (err)
   {
      printf("Invalid Argument to asctime_s.");
   }

   printf( "Coordinated universal time is %s\n",
           buf );
}
```

```Output
Coordinated universal time is Fri Apr 25 20:12:33 2003
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>

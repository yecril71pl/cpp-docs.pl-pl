---
title: _ftime, _ftime32, _ftime64
ms.date: 11/04/2016
api_name:
- _ftime64
- _ftime
- _ftime32
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
- _ftime32
- _ftime
- _ftime64
- ftime64
- ftime
- ftime32
helpviewer_keywords:
- ftime64 function
- _ftime64 function
- current time
- _ftime function
- ftime function
- _ftime32 function
- ftime32 function
- time, getting current
ms.assetid: 96bc464c-3bcd-41d5-a212-8bbd836b814a
ms.openlocfilehash: b8cc46a0a5470892e0bdfdcb0918c2757cdaf4c7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956334"
---
# <a name="_ftime-_ftime32-_ftime64"></a>_ftime, _ftime32, _ftime64

Pobierz bieżącą godzinę. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [_ftime_s, _ftime32_s, _ftime64_s](ftime-s-ftime32-s-ftime64-s.md).

## <a name="syntax"></a>Składnia

```C
void _ftime( struct _timeb *timeptr );
void _ftime32( struct __timeb32 *timeptr );
void _ftime64( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>Parametry

*timeptr*<br/>
Wskaźnik do struktury **_timeb**, **__timeb32**lub **__timeb64** .

## <a name="remarks"></a>Uwagi

Funkcja **_ftime** pobiera bieżącą godzinę lokalną i zapisuje ją w strukturze wskazywanej przez *timeptr*. Struktury **_timeb**, **__timeb32**i **__timeb64** są zdefiniowane w \<pliku sys\\timeb. h >. Zawierają cztery pola, które są wymienione w poniższej tabeli.

|Pole|Opis|
|-|-|
|**dstflag**|Wartość różna od zera, jeśli obowiązuje czas letni dla lokalnej strefy czasowej. (Zobacz [_tzset](tzset.md) , aby dowiedzieć się, jak jest określany czas letni).|
|**millitm**|Część sekundy w milisekundach.|
|**czas**|Czas (w sekundach) od północy (00:00:00), 1 stycznia 1970, uniwersalny czas koordynowany (UTC).|
|**TimeZone**|Różnica w minutach, przesuwanie Westward, między czasem UTC i czasem lokalnym. Wartość **strefy czasowej** jest ustawiana na podstawie wartości zmiennej globalnej **_timezone** (zobacz **_tzset**).|

Funkcja **_ftime64** , która używa struktury **__timeb64** , pozwala na wyrażanie dat tworzenia plików do 23:59:59, 31 grudnia 3000, UTC; **_ftime32** reprezentuje tylko daty do 23:59:59 stycznia 18, 2038, UTC. Północ, 1 stycznia 1970, to Dolna granica zakresu dat dla wszystkich tych funkcji.

Funkcja **_ftime** jest równoważna z **_ftime64**, a **_timeb** zawiera 64-bitowy czas, chyba że **_USE_32BIT_TIME_T** jest zdefiniowany, w takim przypadku stare zachowanie jest stosowane; **_ftime** używa czasu 32-bitowego, a **_timeb** zawiera czas 32-bitowy.

**_ftime** sprawdza poprawność swoich parametrów. Jeśli przeszedł wskaźnik o wartości null jako *timeptr*, funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ustawia **errno** na **EINVAL**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_ftime**|\<sys/typy. h > i \<sys/timeb. h >|
|**_ftime32**|\<sys/typy. h > i \<sys/timeb. h >|
|**_ftime64**|\<sys/typy. h > i \<sys/timeb. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_ftime.c
// compile with: /W3
// This program uses _ftime to obtain the current
// time and then stores this time in timebuffer.

#include <stdio.h>
#include <sys/timeb.h>
#include <time.h>

int main( void )
{
   struct _timeb timebuffer;
   char timeline[26];
   errno_t err;
   time_t time1;
   unsigned short millitm1;
   short timezone1;
   short dstflag1;

   _ftime( &timebuffer ); // C4996
   // Note: _ftime is deprecated; consider using _ftime_s instead

   time1 = timebuffer.time;
   millitm1 = timebuffer.millitm;
   timezone1 = timebuffer.timezone;
   dstflag1 = timebuffer.dstflag;

   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",
   time1);
   printf( "Milliseconds: %d\n", millitm1);
   printf( "Minutes between UTC and local time: %d\n", timezone1);
   printf( "Daylight savings time flag (1 means Daylight time is in "
           "effect): %d\n", dstflag1);

   err = ctime_s( timeline, 26, & ( timebuffer.time ) );
   if (err)
   {
       printf("Invalid argument to ctime_s. ");
   }
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,
           &timeline[20] );
}
```

```Output
Seconds since midnight, January 1, 1970 (UTC): 1051553334
Milliseconds: 230
Minutes between UTC and local time: 480
Daylight savings time flag (1 means Daylight time is in effect): 1
The time is Mon Apr 28 11:08:54.230 2003
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>

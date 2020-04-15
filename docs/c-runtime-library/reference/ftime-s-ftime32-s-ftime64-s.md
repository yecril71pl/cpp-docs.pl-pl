---
title: _ftime_s, _ftime32_s, _ftime64_s
ms.date: 4/2/2020
api_name:
- _ftime_s
- _ftime64_s
- _ftime32_s
- _o__ftime32_s
- _o__ftime64_s
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
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
helpviewer_keywords:
- ftime32_s function
- ftime_s function
- _ftime64_s function
- current time
- ftime64_s function
- time, getting current
- _ftime_s function
- _ftime32_s function
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
ms.openlocfilehash: 0ffd779d8c74b64403837bd973b025da7e3fac2b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345553"
---
# <a name="_ftime_s-_ftime32_s-_ftime64_s"></a>_ftime_s, _ftime32_s, _ftime64_s

Pobiera bieżący czas. Są to wersje [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) z ulepszeniami zabezpieczeń, jak opisano w [programie Funkcje zabezpieczeń w programie CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _ftime_s( struct _timeb *timeptr );
errno_t _ftime32_s( struct __timeb32 *timeptr );
errno_t _ftime64_s( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>Parametry

*timeptr*<br/>
Wskaźnik do **_timeb,** **__timeb32**lub **__timeb64** struktury.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie, kod błędu w przypadku awarii. Jeśli *timepter* ma **wartość NULL**, zwracaną wartością jest **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_ftime_s** pobiera bieżący czas lokalny i przechowuje go w strukturze wskazanej przez *timeptr*. Struktury **_timeb**, **__timeb32**i **__timeb64** są zdefiniowane w pliku SYS\Timeb.h. Zawierają one cztery pola, które są wymienione w poniższej tabeli.

|Pole|Opis|
|-|-|
|**żużel**|Niezerowe, jeśli czas letni jest obecnie w mocy dla lokalnej strefy czasowej. (Zobacz [_tzset,](tzset.md) aby uzyskać wyjaśnienie, w jaki sposób określa się czas letni).|
|**miliitm**|Ułamek sekundy w milisekundach.|
|**Czas**|Czas w sekundach od północy (00:00:00), 1 stycznia 1970, czas uniwersalny (UTC).|
|**Strefa czasowa**|Różnica w minutach, przesuwając się na zachód, między CZASEM UTC a czasem lokalnym. Wartość **strefy czasowej** jest ustawiana na podstawie wartości **zmiennej** globalnej _timezone (patrz **_tzset**).|

Funkcja **_ftime64_s,** która używa **__timeb64** struktury, umożliwia wyrażenie dat tworzenia plików do godziny 23:59:59, 31 grudnia 3000, UTC; mając na **uwadze, że _ftime32_s** reprezentuje tylko daty do 23:59:59 18 stycznia 2038, UTC. Północ, 1 stycznia 1970 r., jest dolną granicą zakresu dat dla wszystkich tych funkcji.

Funkcja **_ftime_s** jest odpowiednikiem **_ftime64_s**i **_timeb** zawiera czas 64-bitowy, chyba że **zdefiniowano _USE_32BIT_TIME_T,** w którym to przypadku obowiązuje stare zachowanie; **_ftime_s** używa czasu 32-bitowego, a **_timeb** zawiera czas 32-bitowy.

**_ftime_s** sprawdza poprawność jego parametrów. Jeśli przeszedł wskaźnik null jako *timepter*, funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [sprawdzanie poprawności parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, funkcja ustawia **errno** na **EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_ftime_s**|\<sys/types.h> i \<sys/timeb.h>|
|**_ftime32_s**|\<sys/types.h> i \<sys/timeb.h>|
|**_ftime64_s**|\<sys/types.h> i \<sys/timeb.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_ftime64_s.c
// This program uses _ftime64_s to obtain the current
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

   _ftime64_s( &timebuffer );

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

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>

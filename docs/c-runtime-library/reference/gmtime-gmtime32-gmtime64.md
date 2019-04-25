---
title: gmtime, _gmtime32, _gmtime64
ms.date: 11/04/2016
apiname:
- _gmtime32
- gmtime
- _gmtime64
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
- gmtime
- _gmtime32
- _gmtime64
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
ms.openlocfilehash: 4f32da5920a0cb892619195207d6501a4b1fd874
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157620"
---
# <a name="gmtime-gmtime32-gmtime64"></a>gmtime, _gmtime32, _gmtime64

Konwertuje **time_t** czasu wartość **tm** struktury. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [gmtime_s —, _gmtime32_s —, _gmtime64_s —](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Składnia

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*sourceTime*<br/>
Wskaźnik na czas przechowywania. Czas jest reprezentowany jako sekundach, które upłynęły od północy (00: 00:00), 1 stycznia 1970 r., skoordynowanego czasu uniwersalnego (UTC).

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury typu [tm](../../c-runtime-library/standard-types.md). Pola zwróconej struktury przechowują ocenianą wartość z *sourceTime* argument w formacie UTC, a nie według czasu lokalnego. Każde z pól struktury jest typu **int**, wykonując następujące czynności:

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
|**tm_isdst**|Zawsze 0 dla **gmtime**.|

Zarówno 32-bitowych i 64-bitowe wersje **gmtime**, [mktime](mktime-mktime32-mktime64.md), [mkgmtime —](mkgmtime-mkgmtime32-mkgmtime64.md), i [localtime](localtime-localtime32-localtime64.md) korzystają z jednej wspólnej **tm**  struktury na wątek dla konwersji. Każde wywołanie jednej z tych funkcji niszczy wynik każdego poprzedniego wywołania. Jeśli *sourceTime* reprezentuje datę wcześniejszą niż północ 1 stycznia 1970 r., **gmtime** zwraca **NULL**. Nie będzie zwrotu błędu.

**_gmtime64**, który używa **__time64_t —** struktury, umożliwia daty do za pośrednictwem 23:59:59, 31 grudnia 3000, czasu UTC, podczas gdy **_gmtime32** przedstawia tylko daty do 23:59:59 18 stycznia 2038 r. UTC. Północy 1 stycznia 1970 r., to dolna granica zakresu dat dla obu tych funkcji.

**gmtime** jest funkcją śródwierszową, której wynikiem **_gmtime64**, i **time_t** jest odpowiednikiem **__time64_t —** chyba że **_USE_32BIT_TIME_ T** jest zdefiniowana. Jeśli trzeba wymusić na kompilatorze interpretowanie **time_t** jako stary 32-bitowy **time_t**, można zdefiniować **_USE_32BIT_TIME_T**, ale wykonanie tego powoduje, że **gmtime** być wyrównane z **_gmtime32** i **time_t** można zdefiniować jako **__time32_t**. Zaleca się, że nie zrobisz, ponieważ nie jest dozwolone na platformach 64-bitowych, a w każdym przypadku aplikacja może przestać działać po 18 stycznia 2038.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *sourceTime* jest wskaźnikiem typu null, lub jeśli *sourceTime* wartość jest ujemna, te wywołają procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje zwracają **NULL** i ustaw **errno** do **EINVAL**.

## <a name="remarks"></a>Uwagi

**_Gmtime32** funkcja dzieli *sourceTime* wartości i zapisuje je w strukturze statycznie przydzielanego typu **tm**zdefiniowaną w czasie. H. Wartość *sourceTime* uzyskuje się zazwyczaj w wyniku wywołania [czasu](time-time32-time64.md) funkcji.

> [!NOTE]
> W większości przypadków środowiska docelowego próbuje określić, czy czas letni obowiązuje. Biblioteki wykonawczej C przyjęto założenie, że używane są zasady Stanów Zjednoczonych wykonywania obliczeń czasu letniego (DST).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek języka C|Wymagany nagłówek C++|
|-------------|---------------------|-|
|**gmtime**, **_gmtime32**, **_gmtime64**|\<time.h>|\<ctime — > lub \<time.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_gmtime.c
// compile with: /W3
// This program uses _gmtime64 to convert a long-
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm *newtime;
   __int64 ltime;
   char buff[80];

   _time64( &ltime );

   // Obtain coordinated universal time:
   newtime = _gmtime64( &ltime ); // C4996
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s
   asctime_s( buff, sizeof(buff), newtime );
   printf( "Coordinated universal time is %s\n", buff );
}
```

```Output
Coordinated universal time is Tue Feb 12 23:11:31 2002
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>

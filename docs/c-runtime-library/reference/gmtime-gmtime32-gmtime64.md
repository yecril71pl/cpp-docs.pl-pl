---
title: gmtime, _gmtime32, _gmtime64
description: Dokumentacja interfejsu API dla gmtime, _gmtime32 i _gmtime64; Konwertowanie wartości time_t na strukturę TM.
ms.date: 4/2/2020
api_name:
- _gmtime32
- gmtime
- _gmtime64
- _o__gmtime32
- _o__gmtime64
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: b3dd09e828b972f05a4c45c30ebc3e5edb68f551
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556466"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>gmtime, _gmtime32, _gmtime64

Konwertuje **time_t** wartość czasu na strukturę **TM** . Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Składnia

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*sourceTime*<br/>
Wskaźnik na czas przechowywania. Czas jest reprezentowany jako sekund, które upłynęły od północy (00:00:00), 1 stycznia 1970, uniwersalny czas koordynowany (UTC).

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury typu [TM](../../c-runtime-library/standard-types.md). Pola zwróconej struktury przechowują obliczoną wartość argumentu *sourceTime* w formacie UTC, a nie w czasie lokalnym. Każde z pól struktury jest typu **`int`** , w następujący sposób:

|Pole|Opis|
|-|-|
|**tm_sec**|Sekund po minucie (0-59).|
|**tm_min**|Minut po godzinie (0-59).|
|**tm_hour**|Godz. od północy (0-23).|
|**tm_mday**|Dzień miesiąca (1-31).|
|**tm_mon**|Miesiąc (0-11; Styczeń = 0).|
|**tm_year**|Year (bieżący rok minus 1900).|
|**tm_wday**|Dzień tygodnia (0-6; Niedziela = 0).|
|**tm_yday**|Dzień roku (0-365; 1 stycznia = 0).|
|**tm_isdst**|Zawsze 0 dla **gmtime**.|

Zarówno 32-bitowe, jak i 64-bitowe wersje **gmtime**, [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)i [localtime](localtime-localtime32-localtime64.md) używają jednej wspólnej struktury **TM** dla każdej wątku dla konwersji. Każde wywołanie jednej z tych funkcji niszczy wynik poprzedniego wywołania. Jeśli *sourceTime* reprezentuje datę sprzed północy, 1 stycznia 1970, **gmtime** zwraca **wartość null**. Nie ma żadnego powrotu błędu.

**_gmtime64**, która korzysta ze struktury **__time64_t** , umożliwia wyrażanie dat do dnia 23:59:59 grudnia, 3000, UTC, a **_gmtime32** tylko daty do 23:59:59 18 stycznia, 2038, UTC. Północ, 1 stycznia 1970, to Dolna granica zakresu dat dla obu funkcji.

**gmtime** to wbudowana funkcja, która oblicza **_gmtime64**, a **time_t** jest równoznaczna z **__time64_t** , chyba że **_USE_32BIT_TIME_T** jest zdefiniowana. Jeśli trzeba wymusić, aby kompilator interpretował **time_t** jako stary **time_t**32-bitowy, można zdefiniować **_USE_32BIT_TIME_T**, ale to spowoduje, że **gmtime** będzie w trybie **_gmtime32** online i **time_t** być zdefiniowane jako **__time32_t**. Firma Microsoft zaleca, aby nie zrobić tego, ponieważ nie jest to dozwolone na 64-bitowych platformach i w każdym przypadku, gdy aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *sourceTime* jest wskaźnikiem typu null lub jeśli wartość *sourceTime* jest ujemna, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje zwracają **wartość null** i ustawiają **errno** na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_gmtime32** przerywa wartość *sourceTime* i zapisuje ją w strukturze statycznie przydzielonym typu **TM**, zdefiniowanej w Time. H. Wartość *sourceTime* jest zazwyczaj uzyskiwana z wywołania funkcji [Time](time-time32-time64.md) .

> [!NOTE]
> W większości przypadków środowisko docelowe próbuje określić, czy obowiązuje czas letni. Biblioteka środowiska uruchomieniowego C zakłada, że używane są reguły Stany Zjednoczone do implementowania obliczeń czasu letniego (DST).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek C|Wymagany nagłówek C++|
|-------------|---------------------|-|
|**gmtime**, **_gmtime32**, **_gmtime64**|\<time.h>|\<ctime> lub \<time.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>

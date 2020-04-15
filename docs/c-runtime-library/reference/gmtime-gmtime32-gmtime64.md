---
title: gmtime, _gmtime32, _gmtime64
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: afa46e583437ebace8edd3a54a6d85e61e02854c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344099"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>gmtime, _gmtime32, _gmtime64

Konwertuje **wartość czasu time_t** na strukturę **tm.** Dostępne są bezpieczniejsze wersje tych funkcji; zobacz [gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Składnia

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*źródłoCzas*<br/>
Wskaźnik do zapisanego czasu. Czas jest reprezentowany jako sekundy upłynęło od północy (00:00:00), 1 stycznia 1970, skoordynowany czas uniwersalny (UTC).

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury typu [tm](../../c-runtime-library/standard-types.md). Pola zwracanej struktury przechowują obliczoną wartość *argumentu sourceTime* w czasie UTC, a nie w czasie lokalnym. Każde z pól struktury jest typu **int, w**następujący sposób:

|Pole|Opis|
|-|-|
|**tm_sec**|Sekundy po minucie (0 - 59).|
|**tm_min**|Minuty po godzinie (0 - 59).|
|**tm_hour**|Godziny od północy (0 - 23).|
|**tm_mday**|Dzień miesiąca (1 - 31).|
|**tm_mon**|Miesiąc (0 - 11; styczeń = 0).|
|**tm_year**|rok (rok bieżący minus 1900).|
|**tm_wday**|Dzień tygodnia (0 - 6; niedziela = 0).|
|**tm_yday**|Dzień roku (0 - 365; 1 stycznia = 0).|
|**tm_isdst**|Zawsze 0 dla **gmtime**.|

Zarówno 32-bitowe, jak i 64-bitowe wersje **gmtime**, [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)i [localtime](localtime-localtime32-localtime64.md) używają jednej wspólnej struktury **tm** na wątek do konwersji. Każde wywołanie jednej z tych funkcji niszczy wynik poprzedniego wywołania. Jeśli *sourceTime* reprezentuje datę przed północą, 1 stycznia 1970 **r., gmtime** zwraca **wartość NULL**. Nie ma zwracania błędów.

**_gmtime64**, która wykorzystuje strukturę **__time64_t,** umożliwia wyrażenie dat do 23:59:59, 31 grudnia 3000, UTC, podczas gdy **_gmtime32** reprezentują tylko daty do 23:59:59 18 stycznia 2038, UTC. Północ, 1 stycznia 1970 r., jest dolną granicą zakresu dat dla obu funkcji.

**gmtime** jest funkcją wbudowaną, która ocenia **_gmtime64**, a **time_t** jest odpowiednikiem **__time64_t,** chyba że **_USE_32BIT_TIME_T** jest zdefiniowany. Jeśli musisz wymusić kompilator do interpretacji **time_t** jako stare **time_t**32-bitowe, można zdefiniować **_USE_32BIT_TIME_T**, ale powoduje **to, że gmtime** jest w kolejce do **_gmtime32** i **time_t,** które mają być zdefiniowane jako **__time32_t**. Zaleca się, aby tego nie robić, ponieważ nie jest dozwolone na platformach 64-bitowych, a w każdym przypadku aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038.

Te funkcje sprawdzają ich parametry. Jeśli *sourceTime* jest wskaźnikiem null lub jeśli *sourceTime* wartość jest ujemna, te funkcje wywołać nieprawidłowy program obsługi parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, funkcje zwracają **null** i ustawić **errno** do **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_gmtime32** dzieli wartość *sourceTime* i przechowuje ją w statycznie przydzielonej strukturze typu **tm,** zdefiniowanej w czas. H. Wartość *sourceTime* jest zazwyczaj uzyskiwana z wywołania funkcji [czasu.](time-time32-time64.md)

> [!NOTE]
> W większości przypadków środowisko docelowe próbuje określić, czy czas letni jest w mocy. Biblioteka wykonawcza języka C zakłada, że używane są reguły Stanów Zjednoczonych dotyczące implementowania obliczania czasu letniego (DST).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek C|Wymagany nagłówek języka C++|
|-------------|---------------------|-|
|**_gmtime32**, **_gmtime32** **_gmtime64**|\<> time.h|\<> czasu lub \<> czasu.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

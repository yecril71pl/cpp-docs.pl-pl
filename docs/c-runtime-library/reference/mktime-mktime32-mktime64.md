---
title: mktime, _mktime32, _mktime64 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mktime32
- mktime
- _mktime64
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
- mktime
- _mktime64
dev_langs:
- C++
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1cc8fbe595259b0f5e59d3ac844710222042540c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206071"
---
# <a name="mktime-mktime32-mktime64"></a>mktime, _mktime32, _mktime64

Konwertuj lokalnego czasu na wartość kalendarza.

## <a name="syntax"></a>Składnia

```C
time_t mktime(
   struct tm *timeptr
);
__time32_t _mktime32(
   struct tm *timeptr
);
__time64_t _mktime64(
   struct tm *timeptr
);
```

### <a name="parameters"></a>Parametry

*timeptr*<br/>
Wskaźnik do struktury czas; zobacz [asctime —](asctime-wasctime.md).

## <a name="return-value"></a>Wartość zwracana

**_mktime32** zwraca czas określony kalendarz zakodowane jako wartość typu [time_t](../../c-runtime-library/standard-types.md). Jeśli *timeptr* odwołuje się do datę wcześniejszą niż północ 1 stycznia 1970 r., lub jeśli nie można przedstawić czas w kalendarzu, **_mktime32** zwraca wartość -1 rzutowane na typ **time_t**. Korzystając z **_mktime32** i, jeśli *timeptr* odwołuje się do datę wypadającą po 23:59:59 18 stycznia 2038 r. uniwersalnego czasu koordynowanego (UTC), to zostanie zwrócona wartość -1 rzutowane na typ **time_t**.

**_mktime64** zostanie zwrócona wartość -1 rzutowane na typ **__time64_t —** Jeśli *timeptr* odwołuje się do datę wypadającą po 23:59:59, 31 grudnia 3000, czasu UTC.

## <a name="remarks"></a>Uwagi

**Mktime**, **_mktime32** i **_mktime64** funkcji konwertuje struktury podany czas (prawdopodobnie niezakończone) wskazywany przez *timeptr*w pełni zdefiniowana strukturę za pomocą znormalizowanych wartości, a następnie konwertuje ją na **time_t** wartość godziny w kalendarzu. Czas przekonwertowany ma tego samego kodu jako wartości zwracane przez [czasu](time-time32-time64.md) funkcji. Oryginalne wartości parametru **tm_wday** i **tm_yday** składniki *timeptr* struktury są ignorowane i oryginalne wartości inne składniki nie są ograniczone Aby ich przewidziane zakresy.

**mktime** jest funkcją śródwierszową, który jest odpowiednikiem **_mktime64**, chyba że **_USE_32BIT_TIME_T** jest zdefiniowany, w którym to przypadku jest to równoważne **_mktime32** .

Po dostosowaniu względem czasu UTC **_mktime32** obsługuje daty od północy 1 stycznia 1970 r., do 23:59:59 18 stycznia 2038 r. UTC. **_mktime64** obsługuje daty od północy 1 stycznia 1970 r. do 23:59:59, 31 grudnia 3000. To dostosowanie może spowodować, że te funkcje, aby zwracają wartość -1 (rzutowany **time_t**, **__time32_t** lub **__time64_t —**), nawet jeśli daty należy określić znajduje się w zakresie. Na przykład, jeśli znajdują się w Kair, Egipt, czyli dwie godziny wyprzedzające czas UTC, dwie godziny zostanie najpierw odjęta od daty, określ w *timeptr*; to, że teraz umieścić swoją datę poza zakresem.

Te funkcje mogą służyć do sprawdzania poprawności, a następnie wypełnij struktury tm. Jeśli operacja się powiedzie, te funkcje ustawiają wartości **tm_wday** i **tm_yday** odpowiednio ustawić innych składników do reprezentowania czas określony kalendarz, ale z wartościami zmuszeni do normalnego zakresy. Końcowa wartość **tm_mday** nie jest ustawiony do momentu **tm_mon** i **tm_year** są określane. Podczas określania **tm** struktury czasu, ustaw **tm_isdst** pola:

- Zero (0), aby wskazać, czy (czas standardowy) jest aktywna.

- Wartość większą niż 0, aby wskazać, że czasu letniego obowiązuje.

- Wartość niższą niż zero, kod biblioteki wykonawczej C obliczeń, czy (czas standardowy) lub czasu jest aktywna.

Biblioteki wykonawczej C określają zachowanie w czasie oszczędność czasu letniego z [TZ](tzset.md) zmiennej środowiskowej. Jeśli **TZ** nie jest ustawiona, wywołanie interfejsu API Win32 [Funkcja GetTimeZoneInformation](https://msdn.microsoft.com/library/windows/desktop/ms724421.aspx) jest używany, aby uzyskać informacje dotyczące czasu letniego z systemu operacyjnego. W przypadku niepowodzenia biblioteki przyjęto założenie, że używane są zasady Stanów Zjednoczonych wykonywania obliczeń czasu letniego. **tm_isdst** jest polem wymaganym. Jeśli nie jest ustawiony, jego wartość jest niezdefiniowana, i wartość zwrotną z tych funkcji, będzie nieprzewidywalny. Jeśli *timeptr* wskazuje **tm** struktury zwrócony przez poprzednie wywołanie [asctime —](asctime-wasctime.md), [gmtime](gmtime-gmtime32-gmtime64.md), lub [localtime](localtime-localtime32-localtime64.md) (lub wariantów tych funkcji) **tm_isdst** pole zawiera poprawną wartość.

Należy pamiętać, że **gmtime** i **localtime** (i **_gmtime32**, **_gmtime64**, **_localtime32**, i **_localtime64**) pojedynczy bufor dla każdego wątku na użytek konwersji. Jeśli podasz tego buforu do **mktime**, **_mktime32** lub **_mktime64**, poprzednie zawartość zostaje zniszczona.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *timeptr* jest pustym wskaźnikiem, wywoływany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość -1 i ustaw **errno** do **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mktime**|\<time.h>|
|**_mktime32**|\<time.h>|
|**_mktime64**|\<time.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_mktime.c
/* The example takes a number of days
* as input and returns the time, the current
* date, and the specified number of days.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm  when;
   __time64_t now, result;
   int        days;
   char       buff[80];

   time( &now );
   _localtime64_s( &when, &now );
   asctime_s( buff, sizeof(buff), &when );
   printf( "Current time is %s\n", buff );
   days = 20;
   when.tm_mday = when.tm_mday + days;
   if( (result = mktime( &when )) != (time_t)-1 ) {
      asctime_s( buff, sizeof(buff), &when );
      printf( "In %d days the time will be %s\n", days, buff );
   } else
      perror( "mktime failed" );
}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Current time is Fri Apr 25 13:34:07 2003

In 20 days the time will be Thu May 15 13:34:07 2003
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>

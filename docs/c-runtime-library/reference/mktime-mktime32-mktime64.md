---
title: mktime —, _mktime32 —, _mktime64 — | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6d02ae8e38a0d3e3b56b5ae69ddd937ef99d76b2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405363"
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

**_mktime32 —** zwraca czas określony kalendarz zakodowane jako wartość typu [time_t —](../../c-runtime-library/standard-types.md). Jeśli *timeptr* odwołuje się do daty przed północy, 1 stycznia 1970, lub jeśli nie można przedstawić czas kalendarza, **_mktime32 —** zwraca wartość -1 rzutowany na typ **time_t —**. Korzystając z **_mktime32 —** i jeśli *timeptr* odwołuje się do daty po 23:59:59 18 stycznia 2038 r. uniwersalnego czasu koordynowanego (UTC), zwróci wartość -1 rzutowany na typ **time_t —**.

**_mktime64 —** zwróci wartość -1 rzutowany na typ **__time64_t —** Jeśli *timeptr* odwołuje się datę wypadającą po 23:59:59 31 grudnia 3000 UTC.

## <a name="remarks"></a>Uwagi

**Mktime —**, **_mktime32 —** i **_mktime64 —** funkcji konwertuje struktury podany czas (prawdopodobnie niepełny) wskazywana przez *timeptr*w pełni zdefiniowanej strukturze z znormalizowanych wartości, a następnie konwertuje go do **time_t —** kalendarza wartości godziny. Czas przekonwertowanego ma tego samego kodu jako wartości zwracane przez [czasu](time-time32-time64.md) funkcji. Oryginalne wartości **tm_wday** i **tm_yday** składniki *timeptr* struktury są ignorowane i oryginalne wartości inne składniki nie są ograniczone do ich normalne zakresów.

**mktime —** jest równoważna funkcji wbudowanej **_mktime64 —**, chyba że **_USE_32BIT_TIME_T** jest zdefiniowany w takim przypadku jest odpowiednikiem **_mktime32 —** .

Po dostosowaniu na czas UTC **_mktime32 —** dojść daty od północy, 1 stycznia 1970 do 23:59:59 18 stycznia 2038 r., UTC. **_mktime64 —** dojść daty od północy, 1 stycznia 1970 do 23:59:59 31 grudnia 3000. Dostosowanie to może spowodować tych funkcji zwrócić wartość -1 (rzutować **time_t —**, **__time32_t** lub **__time64_t —**), mimo że możesz określić datę znajduje się w zakresie. Na przykład, jeśli znajdują się w Kairze, Egipt, który jest o dwie godziny przed UTC, dwie godziny zostanie najpierw odjęta od daty w *timeptr*; to, że teraz umieść daty poza zakresem.

Te funkcje mogą służyć do sprawdzania poprawności i wypełnić strukturę tm. Jeśli się powiedzie, te funkcje ustawić wartości **tm_wday** i **tm_yday** odpowiednio i ustaw inne składniki do reprezentowania czas określony kalendarz, ale z wartościami zmuszony do normalnej zakresy. Końcowa wartość **tm_mday** nie jest ustawiony do **tm_mon** i **tm_year** zależą. Podczas określania **tm** struktury czasu, należy ustawić **tm_isdst** pole do:

- Zero (0), aby wskazać (czas standardowy) jest włączona.

- Wartość większą niż 0, aby wskazać czasu letniego jest włączona.

- Wartość mniejszą niż zero, aby kod biblioteki wykonawczej języka C obliczeniowe, czy (czas standardowy) lub czas letni jest włączona.

Biblioteki wykonawcze języka C określają zachowanie czasu letniego oszczędności z [TZ](tzset.md) zmiennej środowiskowej. Jeśli **TZ** nie jest ustawiona, wywołania interfejsu API Win32 [Funkcja GetTimeZoneInformation](http://msdn.microsoft.com/library/windows/desktop/ms724421.aspx) pozwala uzyskać informacje dotyczące czasu letniego z systemu operacyjnego. Jeśli to się nie powiedzie, biblioteki przyjęto założenie, że są używane zasady wykonywania obliczenia czasu letniego Stanów Zjednoczonych. **tm_isdst** jest polem wymaganym. Jeśli nie ustawiona, jego wartość jest niezdefiniowana i wartość zwrotną z tych funkcji, będzie nieprzewidywalny. Jeśli *timeptr* wskazuje **tm** struktury zwrócony przez poprzednie wywołanie [asctime —](asctime-wasctime.md), [gmtime —](gmtime-gmtime32-gmtime64.md), lub [konwersję](localtime-localtime32-localtime64.md) (lub wariantów tych funkcji), **tm_isdst** pole zawiera poprawną wartość.

Należy pamiętać, że **gmtime —** i **konwersję** (i **_gmtime32 —**, **_gmtime64 —**, **_localtime32 —**, i **_localtime64 —**) do konwersji użyj pojedynczego buforu na wątek. Jeśli podasz tego buforu do **mktime —**, **_mktime32 —** lub **_mktime64 —**, poprzednia zawartość zostaną zniszczone.

Te funkcje sprawdzania poprawności ich parametrów. Jeśli *timeptr* wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli może kontynuować wykonywania, funkcje i ustaw **errno** do **einval —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mktime**|\<time.h>|
|**_mktime32**|\<time.h>|
|**_mktime64**|\<time.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

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

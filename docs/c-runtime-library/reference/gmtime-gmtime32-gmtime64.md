---
title: gmtime —, _gmtime32 —, _gmtime64 — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28ce8b8e2367e1d4dd26672206557867c07827e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403963"
---
# <a name="gmtime-gmtime32-gmtime64"></a>gmtime, _gmtime32, _gmtime64

Konwertuje **time_t —** czasu wartość **tm** struktury. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [gmtime_s —, _gmtime32_s —, _gmtime64_s —](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Składnia

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*sourceTime*<br/>
Wskaźnik do czasu przechowywane. Czas jest przedstawiona w postaci sekund, jaka upłynęła od północy (00: 00:00), 1 stycznia 1970, uniwersalny czas koordynowany (UTC).

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury typu [tm](../../c-runtime-library/standard-types.md). Pola struktury zwrócony przechowywać oceniana wartość *sourceTime* argument w formacie UTC, a nie czas lokalny. Każde z pól struktury jest typu **int**w następujący sposób:

|Pole|Opis|
|-|-|
|**tm_sec**|Sekund po minucie (0 - 59).|
|**tm_min**|Minut po godziny (0 - 59).|
|**tm_hour**|Godziny od północy (0 - 23).|
|**tm_mday**|Dzień miesiąca (1-31).|
|**tm_mon**|Miesiąc (0 - 11; Stycznia = 0).|
|**tm_year**|Rok (bieżącego roku minus 1900).|
|**tm_wday**|Dzień tygodnia (0 – 6; Niedziela = 0).|
|**tm_yday**|Dzień roku (0 - 365; 1 stycznia = 0).|
|**tm_isdst**|Zawsze 0 dla **gmtime —**.|

Zarówno 32-bitowe i 64-bitowe wersje **gmtime —**, [mktime —](mktime-mktime32-mktime64.md), [mkgmtime —](mkgmtime-mkgmtime32-mkgmtime64.md), i [konwersję](localtime-localtime32-localtime64.md) używają co typowe **tm**  struktury na wątek przy konwersji. Każde wywołanie do jednej z tych funkcji niszczy wynik wszelkie poprzednie wywołanie. Jeśli *sourceTime* reprezentuje datę przed północy, 1 stycznia 1970 **gmtime —** zwraca **NULL**. Nie ma żadnych zwracany błąd.

**_gmtime64 —**, który korzysta z **__time64_t —** struktury, umożliwia daty wyrażane się za pośrednictwem 23:59:59 31 grudnia 3000 UTC, podczas gdy **_gmtime32 —** reprezentuje tylko daty do 23:59:59 18 stycznia 2038 r., czasu UTC. Północy, 1 stycznia 1970 jest dolna granica zakresu dat dla obu tych funkcji.

**gmtime —** jest wbudowaną funkcją, która daje w wyniku **_gmtime64 —**, i **time_t —** jest odpowiednikiem **__time64_t —** chyba że **_USE_32BIT_TIME_ T** jest zdefiniowany. Jeśli trzeba wymusić kompilatora, aby zinterpretować **time_t —** jako starego 32-bitowych **time_t —**, można zdefiniować **_USE_32BIT_TIME_T**, ale czynności spowoduje **gmtime —** się w wyrównany do **_gmtime32 —** i **time_t —** określone jako **__time32_t**. Zaleca się, że nie zrobisz, ponieważ nie jest dozwolona na platformach 64-bitowych, a w każdym przypadku aplikacji może zakończyć się niepowodzeniem po 18 stycznia 2038.

Te funkcje walidację ich parametrów. Jeśli *sourceTime* jest wskaźnika o wartości null, lub jeśli *sourceTime* wartość jest liczbą ujemną, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcje zwracają **NULL** i ustaw **errno** do **einval —**.

## <a name="remarks"></a>Uwagi

**_Gmtime32 —** funkcja dzieli *sourceTime* wartość i zapisuje go w strukturze statycznie przydzielonego typu **tm**zdefiniowanej w czasie. H. Wartość *sourceTime* jest zazwyczaj uzyskiwane z wywołania [czasu](time-time32-time64.md) funkcji.

> [!NOTE]
> W większości przypadków środowiska docelowego próbuje określić, czy czasu letniego jest włączona. Biblioteki wykonawcze języka C przy założeniu, że zasady Stanów Zjednoczonych wykonywania obliczeń czasu (DST) są.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek C|Wymagany nagłówek C++|
|-------------|---------------------|-|
|**gmtime —**, **_gmtime32 —**, **_gmtime64 —**|\<time.h>|\<ctime — > lub \<time.h >|

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

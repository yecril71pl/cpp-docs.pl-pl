---
title: gmtime_s —, _gmtime32_s —, _gmtime64_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b15896ff9ec96ed8dd9867c14d252edaad2c67a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405279"
---
# <a name="gmtimes-gmtime32s-gmtime64s"></a>gmtime_s, _gmtime32_s, _gmtime64_s

Konwertuje wartość czasu **tm** struktury. Są to wersje [_gmtime32 —, _gmtime64 —](gmtime-gmtime32-gmtime64.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Wskaźnik do [tm](../../c-runtime-library/standard-types.md) struktury. Pola struktury zwrócony przechowywać oceniana wartość *czasomierza* argument w formacie UTC, a nie czas lokalny.

*sourceTime*<br/>
Wskaźnik do czasu przechowywane. Czas jest przedstawiona w postaci sekund, jaka upłynęła od północy (00: 00:00), 1 stycznia 1970, uniwersalny czas koordynowany (UTC).

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie. Wartość zwracana jest kod błędu w przypadku awarii. Kody błędów są zdefiniowane w Errno.h; Aby uzyskać listę tych błędów, zobacz [errno](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Warunki błędów

|*tmDest*|*sourceTime*|Zwraca|Wartość w *tmDest*|
|-----------|------------|------------|--------------------|
|**NULL**|wszystkie|**EINVAL —**|Nie modyfikować.|
|Nie **NULL** (wskazuje prawidłowy pamięci)|**NULL**|**EINVAL —**|Wszystkie pola ustawioną wartość -1.|
|Nie **wartości NULL**|< 0|**EINVAL —**|Wszystkie pola ustawioną wartość -1.|

W przypadku pierwszego warunków dwóch błędów, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwracać **einval —**.

## <a name="remarks"></a>Uwagi

**_Gmtime32_s —** funkcja dzieli *sourceTime* wartość i zapisuje go w strukturze typu **tm**zdefiniowanej w Time.h. Przekazany adres struktury *tmDest*. Wartość *sourceTime* uzyskuje się zwykle w wyniku wywołania [czasu](time-time32-time64.md) funkcji.

> [!NOTE]
> Środowisko docelowe należy dążyć do określenia czy czasu letniego jest włączona. Biblioteki wykonawcze języka C zakłada Stanów Zjednoczonych zasady wykonywania obliczeń okresu obowiązywania czasu letniego.

Każde z pól struktury jest typu **int**, jak pokazano w poniższej tabeli.

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
|**tm_isdst**|Zawsze 0 dla **gmtime_s —**.|

**_gmtime64_s —**, który korzysta z **__time64_t —** struktury, umożliwia daty wyrażane się za pośrednictwem 23:59:59 31 grudnia 3000 UTC; podczas gdy **gmtime32_s —** tylko reprezentują dat za pomocą 23:59:59 18 stycznia 2038 r., UTC. Północy, 1 stycznia 1970 jest dolna granica zakresu dat dla obu tych funkcji.

**gmtime_s —** jest wbudowaną funkcją, która daje w wyniku **_gmtime64_s —** i **time_t —** jest odpowiednikiem **__time64_t —**. Aby wymusić kompilatora, aby zinterpretować **time_t —** jako starego 32-bitowych **time_t —**, można zdefiniować **_USE_32BIT_TIME_T**. To spowoduje **gmtime_s —** się w wyrównany do **_gmtime32_s —**. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 r., a nie jest dozwolona na platformach 64-bitowych.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek C|Wymagany nagłówek C++|
|-------------|---------------------|-|
|**gmtime_s**|, **_gmtime32_s —**, **_gmtime64_s —**|\<time.h>|\<ctime — > lub \<time.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

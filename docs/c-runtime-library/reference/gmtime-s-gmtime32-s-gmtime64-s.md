---
title: gmtime_s, _gmtime32_s, _gmtime64_s
ms.date: 4/2/2020
api_name:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
- _o__gmtime32_s
- _o__gmtime64_s
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
ms.openlocfilehash: e73d2d3cca852b657631361d8271bec7f9c86ac5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344080"
---
# <a name="gmtime_s-_gmtime32_s-_gmtime64_s"></a>gmtime_s, _gmtime32_s, _gmtime64_s

Konwertuje wartość czasu na strukturę **tm.** Są to wersje [_gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md) z ulepszeniami zabezpieczeń, jak opisano w [programie Funkcje zabezpieczeń w programie CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*tmDest ( tmDest )*<br/>
Wskaźnik do struktury [tm.](../../c-runtime-library/standard-types.md) Pola zwróconej struktury przechowują obliczoną wartość argumentu *czasomierza* w czasie UTC, a nie w czasie lokalnym.

*źródłoCzas*<br/>
Wskaźnik do przechowywanego czasu. Czas jest reprezentowany jako sekundy upłynęło od północy (00:00:00), 1 stycznia 1970, skoordynowany czas uniwersalny (UTC).

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie. Zwracana wartość jest kodem błędu w przypadku wystąpienia błędu. Kody błędów są zdefiniowane w Errno.h; aby uzyskać listę tych błędów, zobacz [errno](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Warunki błędu

|*tmDest ( tmDest )*|*źródłoCzas*|Zwraca|Wartość w *tmDest*|
|-----------|------------|------------|--------------------|
|**Null**|Wszelki|**Einval**|Nie zmodyfikowano.|
|Nie **NULL** (punkty do prawidłowej pamięci)|**Null**|**Einval**|Wszystkie pola ustawione na -1.|
|Nie **NULL**|< 0|**Einval**|Wszystkie pola ustawione na -1.|

W przypadku pierwszych dwóch warunków błędu wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w obszarze [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje **ustawiają errno** na **EINVAL** i zwracają **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_gmtime32_s** dzieli wartość *sourceTime* i przechowuje ją w strukturze typu **tm,** zdefiniowanej w pliku Time.h. Adres struktury jest przekazywany w *tmDest*. Wartość *sourceTime* jest zwykle uzyskiwana z wywołania funkcji [czasu.](time-time32-time64.md)

> [!NOTE]
> Środowisko docelowe należy spróbować określić, czy czas letni jest w mocy. Biblioteka wykonawcza języka C przyjmuje reguły Stanów Zjednoczonych dotyczące wdrażania obliczania czasu letniego.

Każde z pól struktury jest typu **int**, jak pokazano w poniższej tabeli.

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
|**tm_isdst**|Zawsze 0 dla **gmtime_s**.|

**_gmtime64_s**, która wykorzystuje strukturę **__time64_t,** pozwala na wyrażenie dat do 23:59:59, 31 grudnia 3000, UTC; mając na **uwadze, że gmtime32_s** reprezentują tylko daty do 23:59:59 18 stycznia 2038, UTC. Midnight, 1 stycznia 1970, jest dolną granicą zakresu dat dla obu tych funkcji.

**gmtime_s** jest funkcją wbudowaną, która ocenia **_gmtime64_s** i **time_t** jest odpowiednikiem **__time64_t**. Jeśli konieczne jest wymuszenie, aby kompilator interpretował **time_t** jako stary **time_t**32-bitowy, można zdefiniować **_USE_32BIT_TIME_T**. W ten sposób **gmtime_s** będzie w kolejce do **_gmtime32_s**. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 r. i nie jest dozwolona na platformach 64-bitowych.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek C|Wymagany nagłówek języka C++|
|-------------|---------------------|-|
|**gmtime_s** **, _gmtime32_s**, **_gmtime64_s**|\<> time.h|\<> czasu lub \<> czasu.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>

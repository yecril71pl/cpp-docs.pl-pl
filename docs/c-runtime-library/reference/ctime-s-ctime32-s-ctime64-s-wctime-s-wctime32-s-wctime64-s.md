---
title: ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s
ms.date: 11/04/2016
apiname:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
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
- ctime64_s
- _ctime32_s
- _tctime32_s
- _ctime64_s
- _wctime_s
- _tctime_s
- _tctime64_s
- ctime_s
- ctime32_s
helpviewer_keywords:
- _wctime32_s function
- ctime64_s function
- _tctime64_s function
- _wctime_s function
- tctime_s function
- _wctime64_s function
- ctime_s function
- ctime32_s function
- _ctime64_s function
- tctime64_s function
- wctime64_s function
- wctime_s function
- _tctime_s function
- tctime32_s function
- wctime32_s function
- time, converting
- _ctime32_s function
- _tctime32_s function
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
ms.openlocfilehash: 0410aeda4bbec33738d01a9514181c19f351e2c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288364"
---
# <a name="ctimes-ctime32s-ctime64s-wctimes-wctime32s-wctime64s"></a>ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s

Konwertuj na wartość godziny na ciąg, a następnie dostosować ustawienia strefy czasu lokalnego. Są to wersje [ctime, _ctime64, _wctime, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t ctime_s(
   char* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _ctime32_s(
   char* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _ctime64_s(
   char* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime )
;
errno_t _wctime_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _wctime32_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _wctime64_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime
);
```

```cpp
template <size_t size>
errno_t _ctime32_s(
   char (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _ctime64_s(
   char (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime32_s(
   wchar_t (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime64_s(
   wchar_t (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Musi być wystarczająco duży, aby pomieścić 26 znaków. Wskaźnik wynikowy ciąg znaków, lub **NULL** jeśli:

- *sourceTime* reprezentuje datę wcześniejszą o północy, 1 stycznia 1970 r., czasu UTC.

- Jeśli używasz **_ctime32_s** lub **_wctime32_s** i *sourceTime* reprezentuje datę wypadającą po 23:59:59 18 stycznia 2038 r. UTC.

- Jeśli używasz **_ctime64_s —** lub **_wctime64_s —** i *sourceTime* reprezentuje datę wypadającą po 23:59:59, 31 grudnia 3000, czasu UTC.

- Jeśli używasz **_ctime_s** lub **_wctime_s —**, te funkcje są otoki do poprzedniej funkcji. Zobacz sekcję Uwagi.

*numberOfElements*<br/>
Rozmiar buforu.

*sourceTime*<br/>
Wskaźnik na czas przechowywania.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie. W przypadku awarii ze względu na nieprawidłowy parametr, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwracany jest kod błędu. Kody błędów są definiowane w numer błędu. GODZ.; Aby uzyskać listę tych błędów, zobacz [errno](../../c-runtime-library/errno-constants.md). Kody błędu zgłoszony poszczególnych warunków wystąpienia błędu są wyświetlane w poniższej tabeli.

## <a name="error-conditions"></a>Warunki błędów

|*buffer*|*numberOfElements*|*sourceTime*|Wróć|Wartość w *buforu*|
|--------------|------------------------|------------|------------|-----------------------|
|**NULL**|Wszystkie|Wszystkie|**EINVAL**|Nie zmodyfikowano|
|Nie **NULL** (wskazuje prawidłowy pamięci)|0|Wszystkie|**EINVAL**|Nie zmodyfikowano|
|Nie **o wartości NULL**|0 < < 26 rozmiar|Wszystkie|**EINVAL**|Pusty ciąg|
|Nie **o wartości NULL**|>= 26|NULL|**EINVAL**|Pusty ciąg|
|Nie **o wartości NULL**|>= 26|< 0|**EINVAL**|Pusty ciąg|

## <a name="remarks"></a>Uwagi

**Ctime_s** funkcja konwertuje wartość czasu, przechowywane jako [time_t](../../c-runtime-library/standard-types.md) struktury na ciąg znaków. *SourceTime* wartość zwykle jest uzyskiwana w wyniku wywołania [czasu](time-time32-time64.md), która zwraca liczbę sekund, które upłynęły od północy (00: 00:00), 1 stycznia 1970 r., skoordynowanego czasu uniwersalnego (UTC). Ciągu wartość zwracana zawiera dokładnie 26 znaków i ma postać:

`Wed Jan 02 02:03:55 1980\n\0`

Używany jest zegar 24-godzinny. Wszystkie pola są stałej szerokości. Znak nowego wiersza (\n) i znak null (\0) zajmują się dwie ostatnie pozycje ciągu.

Ciąg przekonwertowany znak również jest dostosowywany zgodnie z ustawieniami strefy czasu lokalnego. Zobacz [czasu](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md), i [localtime32_s —](localtime-s-localtime32-s-localtime64-s.md) funkcji dla informacji na temat konfigurowania lokalnego czasu i [_tzset —](tzset.md) Funkcja dla informacji na temat definiowania środowiska strefy czasowej i zmienne globalne.

**_wctime32_s** i **_wctime64_s —** to wersja znaku dwubajtowego **_ctime32_s** i **_ctime64_s —**; zwracającej wskaźnik do ciągu znaków dwubajtowych. W przeciwnym razie **_ctime64_s —**, **_wctime32_s**, i **_wctime64_s —** zachowują się identycznie do **_ctime32_s**.

**ctime_s** jest funkcją śródwierszową, której wynikiem **_ctime64_s —** i **time_t** jest odpowiednikiem **__time64_t —**. Jeśli chcesz wymusić na kompilatorze interpretowanie **time_t** jako stary 32-bitowy **time_t**, można zdefiniować **_USE_32BIT_TIME_T**. Takie działanie spowoduje **ctime_s** na **_ctime32_s**. Nie jest to zalecane, ponieważ aplikacja może przestać działać po 18 stycznia 2038 r. i nie jest dozwolone na platformach 64-bitowych.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s —**|**ctime_s**|**ctime_s**|**_wctime_s**|
|**_tctime32_s**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s —**|**_ctime64_s —**|**_ctime64_s —**|**_wctime64_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ctime_s**, **_ctime32_s**, **_ctime64_s —**|\<time.h>|
|**_wctime_s —**, **_wctime32_s**, **_wctime64_s —**|\<Time.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_wctime_s.c
// This program gets the current
// time in time_t form and then uses _wctime_s to
// display the time in string form.

#include <time.h>
#include <stdio.h>

#define SIZE 26

int main( void )
{
   time_t ltime;
   wchar_t buf[SIZE];
   errno_t err;

   time( &ltime );

   err = _wctime_s( buf, SIZE, &ltime );
   if (err != 0)
   {
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);
   }
   wprintf_s( L"The time is %s\n", buf );
}
```

```Output
The time is Fri Apr 25 13:03:39 2003
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>

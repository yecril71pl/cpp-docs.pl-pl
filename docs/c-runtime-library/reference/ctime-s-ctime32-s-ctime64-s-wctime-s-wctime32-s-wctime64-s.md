---
title: ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s
ms.date: 4/2/2020
api_name:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
- _o__ctime32_s
- _o__ctime64_s
- _o__wctime32_s
- _o__wctime64_s
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
ms.openlocfilehash: d5121c795ed27c22d20087868f798a4b7f5f5b02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348167"
---
# <a name="ctime_s-_ctime32_s-_ctime64_s-_wctime_s-_wctime32_s-_wctime64_s"></a>ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s

Konwertuj wartość czasu na ciąg i dostosuj ustawienia lokalnej strefy czasowej. Są to wersje [ctime, _ctime64, _wctime, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Buforu*<br/>
Musi być wystarczająco duży, aby pomieścić 26 znaków. Wskaźnik do wyniku ciągu znaku lub **NULL,** jeśli:

- *sourceTime* reprezentuje datę przed północą, 1 stycznia 1970, UTC.

- Jeśli używasz **_ctime32_s** lub **_wctime32_s** a *sourceTime* reprezentuje datę po 23:59:59 18 stycznia 2038, UTC.

- Jeśli używasz **_ctime64_s** lub **_wctime64_s** a *sourceTime* reprezentuje datę po 23:59:59, 31 grudnia 3000, UTC.

- W przypadku korzystania z **_ctime_s** lub **_wctime_s**funkcje te są otokami poprzednich funkcji. Zobacz sekcję Uwagi.

*liczbaOfElements*<br/>
Rozmiar buforu.

*źródłoCzas*<br/>
Wskaźnik do przechowywanego czasu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie. Jeśli wystąpi błąd z powodu nieprawidłowego parametru, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, zwracany jest kod błędu. Kody błędów są zdefiniowane w ERRNO. H; aby uzyskać listę tych błędów, zobacz [errno](../../c-runtime-library/errno-constants.md). Rzeczywiste kody błędów generowane dla każdego warunku błędu są wyświetlane w poniższej tabeli.

## <a name="error-conditions"></a>Warunki błędu

|*Buforu*|*liczbaOfElements*|*źródłoCzas*|Zwraca|Wartość w *buforze*|
|--------------|------------------------|------------|------------|-----------------------|
|**Null**|Wszelki|Wszelki|**Einval**|Nie zmodyfikowano|
|Nie **NULL** (punkty do prawidłowej pamięci)|0|Wszelki|**Einval**|Nie zmodyfikowano|
|Nie **NULL**|0< rozmiar < 26|Wszelki|**Einval**|Pusty ciąg znaków|
|Nie **NULL**|>= 26|NULL|**Einval**|Pusty ciąg znaków|
|Nie **NULL**|>= 26|< 0|**Einval**|Pusty ciąg znaków|

## <a name="remarks"></a>Uwagi

Funkcja **ctime_s** konwertuje wartość czasu przechowywaną jako struktura [time_t](../../c-runtime-library/standard-types.md) na ciąg znaków. Wartość *sourceTime* jest zwykle otrzymywana z wywołania [czasu,](time-time32-time64.md)która zwraca liczbę sekund, które upłynęło od północy (00:00:00), 1 stycznia 1970 r., skoordynowany czas uniwersalny (UTC). Ciąg wartości zwracanej zawiera dokładnie 26 znaków i ma formularz:

`Wed Jan 02 02:03:55 1980\n\0`

Używany jest zegar 24-godzinny. Wszystkie pola mają stałą szerokość. Nowy znak wiersza ('\n') i znak null ('\0') zajmują ostatnie dwie pozycje ciągu.

Przekonwertowany ciąg znaków jest również dostosowywany zgodnie z ustawieniami lokalnej strefy czasowej. Zobacz [czas](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)i [localtime32_s](localtime-s-localtime32-s-localtime64-s.md) funkcje, aby uzyskać informacje na temat konfigurowania czasu lokalnego i funkcji [_tzset,](tzset.md) aby uzyskać informacje na temat definiowania środowiska strefy czasowej i zmiennych globalnych.

**_wctime32_s** i **_wctime64_s** są szeroką wersją **_ctime32_s** i **_ctime64_s;** zwracanie wskaźnika do ciągu znaków szerokoznakowych. W przeciwnym razie **_ctime64_s** **, _wctime32_s**i **_wctime64_s** zachowywać się identycznie jak **_ctime32_s**.

**ctime_s** jest funkcją wbudowaną, która ocenia **_ctime64_s** i **time_t** jest odpowiednikiem **__time64_t**. Jeśli konieczne jest wymuszenie, aby kompilator interpretował **time_t** jako stary **time_t**32-bitowy, można zdefiniować **_USE_32BIT_TIME_T**. Spowoduje **to, że ctime_s** oceni **_ctime32_s**. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 r. i nie jest dozwolona na platformach 64-bitowych.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s**|**ctime_s**|**ctime_s**|**_wctime_s**|
|**_tctime32_s**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s**|**_ctime64_s**|**_ctime64_s**|**_wctime64_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ctime_s** **_ctime32_s** **_ctime64_s**|\<> time.h|
|**_wctime_s** **_wctime32_s** **_wctime64_s**|\<time.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>

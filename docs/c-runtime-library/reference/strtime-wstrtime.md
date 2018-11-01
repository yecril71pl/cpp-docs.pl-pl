---
title: _strtime, _wstrtime
ms.date: 11/04/2016
apiname:
- _wstrtime
- _strtime
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
- _wstrtime
- _strtime
- wstrtime
- strtime
- _tstrtime
helpviewer_keywords:
- strtime function
- _strtime function
- _wstrtime function
- copying time to buffers
- wstrtime function
- tstrtime function
- _tstrtime function
- time, copying
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
ms.openlocfilehash: 9d874321418854a703886eb80ee23ac1cba57fa4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431125"
---
# <a name="strtime-wstrtime"></a>_strtime, _wstrtime

Kopiowanie godziny do buforu. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [_strtime_s —, _wstrtime_s —](strtime-s-wstrtime-s.md).

## <a name="syntax"></a>Składnia

```C
char *_strtime(
   char *timestr
);
wchar_t *_wstrtime(
   wchar_t *timestr
);
template <size_t size>
char *_strtime(
   char (&timestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrtime(
   wchar_t (&timestr)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*timestr*<br/>
Ciąg godziny.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do ciągu wynikowego znak *timestr*.

## <a name="remarks"></a>Uwagi

**_Strtime —** funkcja kopiuje bieżący czas lokalny do bufor wskazywany przez *timestr*. Czas jest w formacie **: mm: ss** gdzie **hh** to dwie cyfry reprezentująca godzinę w 24-godzinnego **mm** to dwie cyfry reprezentujący minut po pełnej godziny i **ss** to dwie cyfry reprezentujący sekund. Na przykład ciąg **18:23:44** reprezentuje 23 minuty i 44 sekund po pełnej godzinie 6 Rozmiar buforu musi być co najmniej 9 bajtów.

**_wstrtime —** to wersja znaku dwubajtowego **_strtime —**; argument i wartość zwracana przez **_wstrtime —** są ciągami znaków dwubajtowych. Funkcje te zachowują się identycznie. Jeśli *timestr* jest **o wartości NULL** wskaźnika lub jeśli *timestr* jest sformatowana nieprawidłowo, Nieprawidłowa procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli wyjątek może być kontynuowane, te funkcje zwracają **NULL** i ustaw **errno** do **EINVAL** Jeśli *timestr* został **NULL** lub ustaw **errno** do **ERANGE** Jeśli *timestr* jest niepoprawnie sformatowana.

W języku C++ funkcje te mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime —**|**_strtime**|**_strtime**|**_wstrtime**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strtime**|\<time.h>|
|**_wstrtime**|\<Time.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strtime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
   char tbuffer [9];
   _strtime( tbuffer ); // C4996
   // Note: _strtime is deprecated; consider using _strtime_s instead
   printf( "The current time is %s \n", tbuffer );
}
```

```Output
The current time is 14:21:44
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>

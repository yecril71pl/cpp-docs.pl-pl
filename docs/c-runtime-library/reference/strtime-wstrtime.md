---
title: _strtime, _wstrtime
ms.date: 11/04/2016
api_name:
- _wstrtime
- _strtime
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: ea4a2b304dc30ec167f8a9094bcf278ff0d31f77
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946559"
---
# <a name="_strtime-_wstrtime"></a>_strtime, _wstrtime

Skopiuj czas do buforu. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [_strtime_s, _wstrtime_s](strtime-s-wstrtime-s.md).

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
Ciąg czasu.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do wynikowego ciągu znaków *timestr*.

## <a name="remarks"></a>Uwagi

Funkcja **_strtime** Kopiuje bieżący czas lokalny do buforu wskazywanym przez *timestr*. Godzina jest formatowana jako **hh: mm: SS** , gdzie **hh** ma dwie cyfry reprezentujące godzinę w notacji 24-godzinnej, **mm** to dwie cyfry reprezentujące minuty poza godzinę, a **SS** to dwie cyfry reprezentujące sekundy. Na przykład ciąg **18:23:44** reprezentuje 23 minuty i 44 s ostatnich 6 godzin Długość buforu musi wynosić co najmniej 9 bajtów.

**_wstrtime** to dwubajtowa wersja **_strtime**; argument i wartość zwracana przez **_wstrtime** są ciągami znaków dwubajtowych. Funkcje te zachowują się identycznie w inny sposób. Jeśli *timestr* jest wskaźnikiem typu **null** lub jeśli *timestr* jest niepoprawnie sformatowany, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wyjątek może być kontynuowany, te funkcje zwracają **wartość null** i ustawiają **errno** na **EINVAL** , jeśli *timestr* była **wartością null** lub ustawiono **errno** do **ERANGE** , jeśli *timestr* jest niepoprawnie sformatowany.

W C++programie te funkcje mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime**|**_strtime**|**_strtime**|**_wstrtime**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strtime**|\<time.h>|
|**_wstrtime**|\<Time. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

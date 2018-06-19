---
title: _strtime —, _wstrtime — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b0ca776394b47f5209fbf034cbb10461c220634
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450787"
---
# <a name="strtime-wstrtime"></a>_strtime, _wstrtime

Skopiuj czas w buforze. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_strtime_s —, _wstrtime_s —](strtime-s-wstrtime-s.md).

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

Zwraca wskaźnik do wynikowy ciąg znaków *timestr*.

## <a name="remarks"></a>Uwagi

**_Strtime —** funkcja bieżącym czasem lokalnym są kopiowane do bufor wskazywany przez *timestr*. Czas jest w formacie **hh: mm:** gdzie **hh** to dwie cyfry reprezentującą godzinę w 24-godzinnego **mm** to dwie cyfry reprezentujący minut po godziny i **ss** to dwie cyfry reprezentujący sekund. Na przykład ciąg **18:23:44** reprezentuje 23 minut i 44 sekund po pełnej godzinie 6 Rozmiar buforu musi być co najmniej 9 bajtów.

**_wstrtime —** jest wersja znaków dwubajtowych **_strtime —**; argumentów i wartości **_wstrtime —** są ciągami znaków dwubajtowych. Funkcje te działają tak samo w przeciwnym razie wartość. Jeśli *timestr* jest **NULL** wskaźnika lub, jeśli *timestr* jest sformatowany nieprawidłowo, nieprawidłowego parametru program obsługi zostanie wywołany, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli wyjątek będzie mógł kontynuować, te funkcje zwracają **NULL** i ustaw **errno** do **einval —** Jeśli *timestr* został **NULL** lub ustaw **errno** do **erange —** Jeśli *timestr* jest niepoprawnie sformatowana.

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują odpowiedników nowsza, bezpieczne tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
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

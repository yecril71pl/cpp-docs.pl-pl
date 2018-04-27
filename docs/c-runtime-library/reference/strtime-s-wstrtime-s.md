---
title: _strtime_s —, _wstrtime_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wstrtime_s
- _strtime_s
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
- _wstrtime_s
- strtime_s
- wstrtime_s
- _strtime_s
dev_langs:
- C++
helpviewer_keywords:
- wstrtime_s function
- copying time to buffers
- strtime_s function
- _wstrtime_s function
- time, copying
- _strtime_s function
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2322f9be760faf36c2443d190229a4c67b47582b
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="strtimes-wstrtimes"></a>_strtime_s, _wstrtime_s

Skopiuj bieżącą godzinę w buforze. Są to wersje [_strtime —, _wstrtime —](strtime-wstrtime.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _strtime_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrtime_s(
   wchar_t *buffer,
   size_t numberOfElements
);
template <size_t size>
errno_t _strtime_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrtime_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Bufor, co najmniej 10 bajtów, którym zostanie zapisany czas.

*numberOfElements*<br/>
Rozmiar buforu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie.

Jeśli wystąpi błąd, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Wartość zwracana jest kod błędu w przypadku awarii. Kody błędów są definiowane w numer błędu. H; Zobacz poniższą tabelę dla dokładnego błędy generowane przez tę funkcję. Aby uzyskać więcej informacji o kodach błędów, zobacz [errno — stałe](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Warunki błędów

|*buffer*|*numberOfElements*|Zwraca|Zawartość *buforu*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|(wszystkie)|**EINVAL —**|Nie zmodyfikowano|
|Nie **NULL** (prawidłowego buforu wskazująca)|0|**EINVAL —**|Nie zmodyfikowano|
|Nie **NULL** (prawidłowego buforu wskazująca)|0 < rozmiaru < 9|**EINVAL —**|Pusty ciąg|
|Nie **NULL** (prawidłowego buforu wskazująca)|Rozmiar > 9|0|Bieżąca godzina sformatowana zgodnie z uwagi|

## <a name="security-issues"></a>Problemy z zabezpieczeniami

Przekazując wartość inną niż NULL jest nieprawidłowa dla buforu będzie spowodować naruszenie zasad dostępu, jeśli *numberOfElements* parametru jest większa niż 9.

Przekazywanie wartości dla *numberOfElements* jest większy niż rzeczywisty rozmiar buforu spowoduje przepełnienie buforu.

## <a name="remarks"></a>Uwagi

Funkcje te zapewniają bardziej bezpieczne wersje [_strtime —](strtime-wstrtime.md) i [_wstrtime —](strtime-wstrtime.md). **_Strtime_s —** funkcja bieżącym czasem lokalnym są kopiowane do bufor wskazywany przez *timestr*. Czas jest w formacie **hh: mm:** gdzie **hh** to dwie cyfry reprezentującą godzinę w 24-godzinnego **mm** to dwie cyfry reprezentujący minut po godziny i **ss** to dwie cyfry reprezentujący sekund. Na przykład ciąg **18:23:44** reprezentuje 23 minut i 44 sekund po pełnej godzinie 6 Rozmiar buforu musi być co najmniej 9 bajtów; Rzeczywisty rozmiar określono za pomocą drugiego parametru.

**_wstrtime —** jest wersja znaków dwubajtowych **_strtime —**; argumentów i wartości **_wstrtime —** są ciągami znaków dwubajtowych. Funkcje te działają tak samo w przeciwnym razie wartość.

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mapping"></a>Rutynowe mapowanie — zwykły tekst:

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime_s**|**_strtime_s**|**_strtime_s**|**_wstrtime_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strtime_s**|\<time.h>|
|**_wstrtime_s**|\<Time.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// strtime_s.c

#include <time.h>
#include <stdio.h>

int main()
{
    char tmpbuf[9];
    errno_t err;

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    // Display operating system-style date and time.
    err = _strtime_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
      exit(1);
    }
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );
    err = _strdate_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
       exit(1);
    }
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );

}
```

```Output
OS time:            14:37:49
OS date:            04/25/03
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>

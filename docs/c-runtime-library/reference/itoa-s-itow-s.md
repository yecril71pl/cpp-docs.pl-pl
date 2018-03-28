---
title: _itoa_s —, _itow_s — funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/21/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _itoa_s
- _ltoa_s
- _ultoa_s
- _i64toa_s
- _ui64toa_s
- _itow_s
- _ltow_s
- _ultow_s
- _i64tow_s
- _ui64tow_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _itoa_s
- _ltoa_s
- _ultoa_s
- _i64toa_s
- _ui64toa_s
- _itow_s
- _ltow_s
- _ultow_s
- _i64tow_s
- _ui64tow_s
- _itot_s
- _ltot_s
- _ultot_s
- _i64tot_s
- _ui64tot_s
- itoa_s
- ltoa_s
- ultoa_s
- i64toa_s
- ui64toa_s
- itow_s
- ltow_s
- ultow_s
- i64tow_s
- ui64tow_s
- itot_s
- ltot_s
- ultot_s
- i64tot_s
- ui64tot_s
dev_langs:
- C++
helpviewer_keywords:
- _ui64toa_s function
- _itow_s function
- _i64tow_s function
- _itot_s function
- converting integers
- itow_s function
- i64toa_s function
- _ui64tow_s function
- integers, converting
- _i64tot_s function
- itoa_s function
- _itoa_s function
- ui64toa_s function
- i64tow_s function
- converting numbers, to strings
- _ui64tot_s function
- _i64toa_s function
ms.assetid: eb746581-bff3-48b5-a973-bfc0a4478ecf
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3598724e905c51c68e7f4305f409060eb1f98e41
ms.sourcegitcommit: 604907f77eb6c5b1899194a9877726f3e8c2dabc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="itoas-ltoas-ultoas-i64toas-ui64toas-itows--ltows--ultows-i64tows-ui64tows"></a>_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s,  _ltow_s,  _ultow_s, _i64tow_s, _ui64tow_s

Konwertuje liczbę całkowitą na ciąg. Są to wersje [_itoa —, funkcje _itow —](../../c-runtime-library/reference/itoa-itow.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _itoa_s( int value, char * buffer, size_t size, int radix );
errno_t _ltoa_s( long value, char * buffer, size_t size, int radix );
errno_t _ultoa_s( unsigned long value, char * buffer, size_t size, int radix );
errno_t _i64toa_s( long long value, char *buffer,
   size_t size, int radix );
errno_t _ui64toa_s( unsigned long long value, char *buffer,
   size_t size, int radix );

errno_t _itow_s( int value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ltow_s( long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ultow_s( unsigned long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _i64tow_s( long long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ui64tow_s( unsigned long long value, wchar_t *buffer,
   size_t size, int radix
);

// These template functions are C++ only:
template <size_t size>
errno_t _itoa_s( int value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _ltoa_s( long value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _ultoa_s( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _itow_s( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
errno_t _ltow_s( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
errno_t _ultow_s( unsigned long value, wchar_t (&buffer)[size], int radix );
```

### <a name="parameters"></a>Parametry

*value*<br/>
Numer do skonwertowania.

*buffer*<br/>
Bufor wyjściowy przechowujący wynik konwersji.

*Rozmiar*<br/>
Rozmiar *buforu* znaków lub znaki dwubajtowe.

*radix*<br/>
Podstawa lub liczbowego base do konwersji *wartość*, która musi być w zakresie od 2 36.

## <a name="return-value"></a>Wartość zwracana

Zero w przypadku powodzenia; błąd o kodzie błędu. Jeśli dowolny z następujących warunków ma zastosowanie funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).

### <a name="error-conditions"></a>Warunki błędów

|value|Bufor|size|radix|Zwraca|
|-----------|------------|----------------------|-----------|------------|
|wszystkie|`NULL`|wszystkie|wszystkie|`EINVAL`|
|wszystkie|wszystkie|<=0|wszystkie|`EINVAL`|
|wszystkie|wszystkie|< = długość ciągu wynik wymagane|wszystkie|`EINVAL`|
|wszystkie|wszystkie|wszystkie|*Podstawa* < 2 lub *radix* > 36|`EINVAL`|

### <a name="security-issues"></a>Problemy z zabezpieczeniami

Funkcje te mogą generować naruszenia zasad dostępu, jeśli *buforu* nie wskazuje na prawidłową pamięci i nie jest `NULL`, lub jeśli długość buforu nie jest wystarczająco długi pomieścić ciąg wyniku.

## <a name="remarks"></a>Uwagi

Z wyjątkiem tych parametrów i zwracanych wartości `_itoa_s` i `_itow_s` rodziny funkcji ma takie samo zachowanie jako odpowiadającego mniej bezpieczne `_itoa` i `_itow` wersji.

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wprowadzić bufor 0xFD. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).

CRT obejmuje wygodny makra, aby zdefiniować rozmiar buforu wymaganych do przekonwertowania najdłuższym możliwa wartość każdego typu Liczba całkowita, włącznie z terminatorem null i zaloguj się znak, dla kilku wspólnej bazy. Aby uzyskać informacje, zobacz [makra Liczba konwersji maksymalnie](itoa-itow.md#maximum-conversion-count-macros).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_itot_s`|`_itoa_s`|`_itoa_s`|`_itow_s`|
|`_ltot_s`|`_ltoa_s`|`_ltoa_s`|`_ltow_s`|
|`_ultot_s`|`_ultoa_s`|`_ultoa_s`|`_ultow_s`|
|`_i64tot_s`|`_i64toa_s`|`_i64toa_s`|`_i64tow_s`|
|`_ui64tot_s`|`_ui64toa_s`|`_ui64toa_s`|`_ui64tow_s`|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_itoa_s`, `_ltoa_s`, `_ultoa_s`, `_i64toa_s`, `_ui64toa_s`|\<stdlib.h>|
|`_itow_s`, `_ltow_s`, `_ultow_s`, `_i64tow_s`, `_ui64tow_s`|\<stdlib.h > lub \<wchar.h >|

Te funkcje są specyficzne dla firmy Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W przykładzie pokazano użycie kilku funkcji konwersja liczby całkowitej. Należy pamiętać, że [_countof —](countof-macro.md) makro działa tylko do określenia rozmiaru buforu, gdy deklaracja tablicy jest widoczny w kompilatorze, a nie parametry, które mają zbutwiałe do wskaźników.

```C
// crt_itoa_s.c
// Compile by using: cl /W4 crt_itoa_s.c
#include <stdlib.h>     // for _itoa_s functions, _countof, count macro
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen

int main( void )
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;
    for ( r = 10; r >= 2; --r )
    {
        _itoa_s( -1, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
    printf( "\n" );
    for ( r = 10; r >= 2; --r )
    {
        _i64toa_s( -1LL, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
    printf( "\n" );
    for ( r = 10; r >= 2; --r )
    {
        _ui64toa_s( 0xffffffffffffffffULL, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
}
```

```Output
base 10: -1 (2 chars)
base 9: 12068657453 (11 chars)
base 8: 37777777777 (11 chars)
base 7: 211301422353 (12 chars)
base 6: 1550104015503 (13 chars)
base 5: 32244002423140 (14 chars)
base 4: 3333333333333333 (16 chars)
base 3: 102002022201221111210 (21 chars)
base 2: 11111111111111111111111111111111 (32 chars)

base 10: -1 (2 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)

base 10: 18446744073709551615 (20 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[_itoa —, _itow — funkcje](../../c-runtime-library/reference/itoa-itow.md)<br/>

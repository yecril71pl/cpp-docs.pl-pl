---
title: mbtowc, _mbtowc_l
ms.date: 11/04/2016
apiname:
- mbtowc
- _mbtowc_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- mbtowc
helpviewer_keywords:
- mbtowc function
- _mbtowc_l function
- mbtowc_l function
ms.assetid: dfd1c8a7-e73a-4307-9353-53b70b45d4d1
ms.openlocfilehash: c02d1a636db75b4a26891a93fa20327b7430443d
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210643"
---
# <a name="mbtowc-mbtowcl"></a>mbtowc, _mbtowc_l

Konwertuj znak wielobajtowy do odpowiedniego szerokiego znaku.

## <a name="syntax"></a>Składnia

```C
int mbtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count
);
int _mbtowc_l(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*WChar*<br/>
Adres znaków dwubajtowych (typ **wchar_t**).

*mbchar*<br/>
Adres sekwencji bajtów (znak wielobajtowy).

*Liczba*<br/>
Liczba bajtów do wyboru.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Jeśli **mbchar** nie jest **NULL** i, jeśli obiekt, *mbchar* wskazuje prawidłowy znak wielobajtowy formularzy **mbtowc** zwraca długość w bajtów znaków wielobajtowych. Jeśli *mbchar* jest **NULL** lub obiekt, który wskazuje na to znak null szerokich znaków (L '\0'), funkcja zwraca 0. Jeśli obiekt, *mbchar* wskazuje nie tworzą prawidłowy znak wielobajtowy w obrębie pierwszych *liczba* znaków, zwraca wartość -1.

## <a name="remarks"></a>Uwagi

**Mbtowc** funkcji konwertuje *liczba* lub mniejsza liczba bajtów wskazywany przez *mbchar*, jeśli *mbchar* nie **wartościNULL**, do odpowiedniego szerokiego znaku. **mbtowc** zapisuje wynikowy znak dwubajtowy na *wchar,* Jeśli *wchar* nie jest **NULL**. **mbtowc** nie analizuje ponad **MB_CUR_MAX** bajtów. **mbtowc** używa bieżących ustawień regionalnych dla zachowań zależnych od ustawień regionalnych; **_mbtowc_l —** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbtowc**|\<stdlib.h>|
|**_mbtowc_l**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_mbtowc.c
// Illustrates the behavior of the mbtowc function

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    int      i;
    char    *pmbc    = (char *)malloc( sizeof( char ) );
    wchar_t  wc      = L'a';
    wchar_t *pwcnull = NULL;
    wchar_t *pwc     = (wchar_t *)malloc( sizeof( wchar_t ) );
    printf( "Convert a wide character to multibyte character:\n" );
    wctomb_s( &i, pmbc, sizeof(char), wc );
    printf( "  Characters converted: %u\n", i );
    printf( "  Multibyte character: %x\n\n", *pmbc );

    printf( "Convert multibyte character back to a wide "
            "character:\n" );
    i = mbtowc( pwc, pmbc, MB_CUR_MAX );
    printf( "   Bytes converted: %u\n", i );
    printf( "   Wide character: %x\n\n", *pwc );
    printf( "Attempt to convert when target is NULL\n" );
    printf( "   returns the length of the multibyte character:\n" );
    i = mbtowc( pwcnull, pmbc, MB_CUR_MAX );
    printf( "   Length of multibyte character: %u\n\n", i );

    printf( "Attempt to convert a NULL pointer to a" );
    printf( " wide character:\n" );
    pmbc = NULL;
    i = mbtowc( pwc, pmbc, MB_CUR_MAX );
    printf( "   Bytes converted: %u\n", i );
}
```

```Output
Convert a wide character to multibyte character:
   Characters converted: 1
   Multibyte character: 61

Convert multibyte character back to a wide character:
   Bytes converted: 1
   Wide character: 61

Attempt to convert when target is NULL
   returns the length of the multibyte character:
   Length of multibyte character: 1

Attempt to convert a NULL pointer to a wide character:
   Bytes converted: 0
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>

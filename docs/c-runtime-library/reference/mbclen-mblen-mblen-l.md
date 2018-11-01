---
title: _mbclen, mblen, _mblen_l
ms.date: 11/04/2016
apiname:
- _mbclen
- mblen
- _mblen_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mblen
- ftclen
- _mbclen
- tclen
- _ftclen
- _tclen
- mbclen
helpviewer_keywords:
- tclen function
- _mblen_l function
- _tclen function
- mblen_l function
- _mbclen function
- mbclen function
- mblen function
ms.assetid: d5eb92a0-b7a3-464a-aaf7-9890a8e3ed70
ms.openlocfilehash: dddf7d3a1705460d2c8d42cc1b36230d7bdaf942
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434389"
---
# <a name="mbclen-mblen-mblenl"></a>_mbclen, mblen, _mblen_l

Pobiera długość i określa ważność znaków wielobajtowych.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
size_t _mbclen(
   const unsigned char *c
);
int mblen(
   const char *mbstr,
   size_t count
);
int _mblen_l(
   const char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak wielobajtowy.

*mbstr*<br/>
Adres sekwencji bajtów znaków wielobajtowych.

*Liczba*<br/>
Liczba bajtów do wyboru.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbclen —** zwraca wartość 1 lub 2, zgodnie z czy znak wielobajtowy *c* to 1 lub 2 bajtów. Błąd nie jest zwracana dla **_mbclen —**. Jeśli *mbstr* nie **NULL**, **mblen —** zwraca długość w bajtach, znaku wielobajtowego. Jeśli *mbstr* jest **NULL** lub wskazuje znak null znaków dwubajtowych, **mblen —** zwraca wartość 0. Jeśli obiekt, *mbstr* wskazuje nie tworzą prawidłowy znak wielobajtowy w obrębie pierwszych *liczba* znaków, **mblen —** zwraca wartość -1.

## <a name="remarks"></a>Uwagi

**_Mbclen —** funkcja zwraca długość w bajtach, znaku wielobajtowego *c*. Jeśli *c* nie wskazuje bajtu wiodącego znaku wielobajtowego jak ustalono przez wywołanie niejawne **_ismbblead**, wynikiem **_mbclen —** jest nieprzewidywalne.

**mblen —** zwraca długość w bajtach *mbstr* prawidłowy znak wielobajtowy i określa ważność znaków wielobajtowych skojarzonych ze stroną kodową. **mblen —** sprawdza *liczba* lub mniejsza liczba bajtów zawartych w *mbstr*, ale nie więcej niż **MB_CUR_MAX** bajtów.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, bez **_l** sufiks używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych w zamian przekazanych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen —**|Mapy i makro lub funkcja śródwierszowa|**_mbclen**|Mapy i makro lub funkcja śródwierszowa|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbclen**|\<mbstring.h>|
|**mblen —**|\<stdlib.h>|
|**_mblen_l**|\<stdlib.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_mblen.c
/* illustrates the behavior of the mblen function
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    int      i;
    char    *pmbc = (char *)malloc( sizeof( char ) );
    wchar_t  wc   = L'a';

    printf( "Convert wide character to multibyte character:\n" );
    wctomb_s( &i, pmbc, sizeof(char), wc );
    printf( "   Characters converted: %u\n", i );
    printf( "   Multibyte character: %x\n\n", *pmbc );

    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of multibyte character %x: %u\n", *pmbc, i );

    pmbc = NULL;
    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of NULL multibyte character %x: %u\n", pmbc, i );
}
```

```Output
Convert wide character to multibyte character:
   Characters converted: 1
   Multibyte character: 61

Length in bytes of multibyte character 61: 1
Length in bytes of NULL multibyte character 0: 0
```

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>

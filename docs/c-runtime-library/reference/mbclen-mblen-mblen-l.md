---
title: _mbclen, mblen, _mblen_l, _mbclen_l
description: W tym artykule opisano _mbclen, mblen, _mblen_l i _mbclen_l.
ms.date: 4/2/2020
api_name:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
- _o__mbclen
- _o__mbclen_l
- _o__mblen_l
- _o_mblen
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mblen
- ftclen
- _mbclen
- _mbclen_l
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
- _mbclen_l function
- mbclen function
- mblen function
ms.assetid: d5eb92a0-b7a3-464a-aaf7-9890a8e3ed70
ms.openlocfilehash: 76e8771898d8baa65f275304a9aefdcaeeb5b3bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341120"
---
# <a name="_mbclen-mblen-_mblen_l-_mbclen_l"></a>_mbclen, mblen, _mblen_l, _mbclen_l

Pobiera długość i określa ważność znaku wielobajtowego.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
size_t _mbclen(
   const unsigned char *c
);
size_t _mbclen_l(
   unsigned char const* c,
   _locale_t locale
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

*C*\
Znak wielobajtowy.

*mbstr*\
Adres sekwencji bajtów wielobajtowych.

*Liczba*\
Liczba bajtów do sprawdzenia.

*Ustawień regionalnych*\
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbclen** i **_mbclen_l** zwracają 1 lub 2, w zależności od długości znaku wielobajtowego *c*. Funkcje zawsze zwracają 1 dla UTF-8, czy *c* jest wielobajtowy, czy nie. Nie ma zwrotu błędu dla **_mbclen**.

Jeśli *mbstr* nie jest **null**, **mblen** i **_mblen_l** zwracać długość w bajtach znaku wielobajtowego. **Mblen** i **_mblen_l** funkcje działają poprawnie na UTF-8 i może zwrócić wartość między 1 i 3. Gdy *mbstr* ma **wartość NULL** (lub wskazuje znak null o szerokim znaku), **mblen** i **_mblen_l** zwracają 0. Obiekt, który *mbstr* wskazuje, musi tworzyć prawidłowy znak wielobajtowy w obrębie pierwszych znaków *zliczania* lub **mblen** i **_mblen_l** zwracać -1.

## <a name="remarks"></a>Uwagi

Funkcja **_mbclen** zwraca długość znaku wielobajtowego *c*w bajtach . Jeśli *c* nie wskazuje na bajt wiodący znaku wielobajtowego (określonego przez niejawne wywołanie [_ismbblead,](ismbblead-ismbblead-l.md)wynik **_mbclen** jest nieprzewidywalny.

**mblen** zwraca długość w bajtach *mbstr,* jeśli jest to prawidłowy znak wielobajtowy. Określa również ważność wielobajtowych znaków skojarzonych ze stroną kodową. **mblen** sprawdza *liczbę* lub mniejszą liczbę bajtów zawartych w *mbstr*, ale nie więcej niż **MB_CUR_MAX** bajtów.

Na wartość danych wyjściowych ma wpływ ustawienie **kategorii LC_CTYPE** ustawień regionalnych. Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. Wersje sufiksów **_l** zachowują się tak samo, ale zamiast tego używają parametru ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md) i [Ustawienia regionalne](../../c-runtime-library/locale.md).

**_mbclen**, **_mblen_l**i **_mbclen_l** są specyficzne dla firmy Microsoft, a nie są częścią biblioteki Standard C. Nie zalecamy używania ich tam, gdzie chcesz przenośny kod. W przypadku zgodności ze standardem C należy użyć **mblen** lub **mbrlen.**

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|Mapowanie do funkcji makra lub wbudowanej|**_mbclen**|Mapowanie do funkcji makra lub wbudowanej|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbclen**|\<mbstring.h>|
|**mblen ( mblen )**|\<>|
|**_mblen_l**|\<>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)\
[Ustawień regionalnych](../../c-runtime-library/locale.md)\
[Interpretacja sekwencji znaków wielobajtowych](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
[_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md)\
[mbrlen (mbrlen)](mbrlen.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)

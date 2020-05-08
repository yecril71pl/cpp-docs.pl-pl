---
title: _mbclen, mblen, _mblen_l, _mbclen_l
description: Opisuje funkcje _mbclen, mblen, _mblen_l i _mbclen_l w bibliotece środowiska uruchomieniowego Microsoft C (CRT).
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b004babc9e7c82d25cd52ec036c3061c99b5f367
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914370"
---
# <a name="_mbclen-mblen-_mblen_l-_mbclen_l"></a>_mbclen, mblen, _mblen_l, _mbclen_l

Pobiera długość i określa ważność znaku wielobajtowego.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*s*\
Znak wielobajtowy.

*mbstr*\
Adres sekwencji bajtów znaków wielobajtowych.

*liczbą*\
Liczba bajtów do sprawdzenia.

*ustawienie*\
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbclen** i **_mbclen_l** zwracać 1 lub 2, zgodnie z długością znaku wielobajtowego *c*. Funkcje zawsze zwracają wartość 1 dla UTF-8, niezależnie od tego, czy *c* jest wielobajtowy, czy nie. Nie ma żadnego powrotu błędu dla **_mbclen**.

Jeśli *mbstr* nie ma **wartości null**, **mblen** i **_mblen_l** zwracają Długość (w bajtach) znaku wielobajtowego. Funkcje **mblen** i **_mblen_l** działają poprawnie w kodowaniu UTF-8 i mogą zwracać wartość z zakresu od 1 do 3. Gdy *mbstr* ma **wartość null** (lub wskazuje znak dwubajtowy o wartości null), **mblen** i **_mblen_l** zwracają 0. Obiekt, który *mbstr* wskazuje, musi tworzyć prawidłowy znak wielobajtowy w obrębie pierwszych znaków *Count* , lub **mblen** i **_mblen_l** zwracać-1.

## <a name="remarks"></a>Uwagi

Funkcja **_mbclen** zwraca długość w bajtach znaku wielobajtowego *c*. Jeśli *c* nie wskazuje bajtu wiodącego znaku wielobajtowego (zgodnie z niejawnym wywołaniem [_ismbblead](ismbblead-ismbblead-l.md), wynik **_mbclen** jest nieprzewidywalny.

**mblen** zwraca długość w bajtach *mbstr* , jeśli jest prawidłowym znakiem wielobajtowym. Określa również ważność znaków wielobajtowych skojarzonych ze stroną kodową. **mblen** bada *liczbę* lub mniejszą liczbę bajtów zawartych w *mbstr*, ale nie więcej niż **MB_CUR_MAX** bajtów.

Wartość wyjściowa jest zależna od ustawienia kategorii **LC_CTYPE** ustawień regionalnych. Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. **_L** wersje sufiksów zachowują się tak samo, ale w zamian używają parametru ustawień regionalnych. Aby uzyskać więcej informacji, zobacz sekcję [setlocale](setlocale-wsetlocale.md) i [locale](../../c-runtime-library/locale.md).

**_mbclen**, **_mblen_l**i **_Mbclen_l** są charakterystyczne dla firmy Microsoft, a nie częścią standardowej biblioteki C. Nie zalecamy korzystania z nich w przypadku, gdy potrzebny jest kod przenośny. W przypadku standardowej zgodności C zamiast tego należy użyć **mblen** lub **mbrlen** .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|Mapuje na makro lub funkcję wbudowaną|**_mbclen**|Mapuje na makro lub funkcję wbudowaną|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbclen**|\<mbstring. h>|
|**mblen**|\<STDLIB. h>|
|**_mblen_l**|\<STDLIB. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
[Ustawienie](../../c-runtime-library/locale.md)\
[Interpretacja sekwencji znaków wielobajtowych](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
[_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md)\
[mbrlen](mbrlen.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)

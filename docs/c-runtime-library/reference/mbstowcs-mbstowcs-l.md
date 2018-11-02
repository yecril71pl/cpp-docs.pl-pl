---
title: mbstowcs, _mbstowcs_l
ms.date: 11/04/2016
apiname:
- mbstowcs
- _mbstowcs_l
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
- mbstowcs
helpviewer_keywords:
- _mbstowcs_l function
- mbstowcs_l function
- mbstowcs function
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
ms.openlocfilehash: b788cd820f1297c563f3db739173162bb4983758
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500974"
---
# <a name="mbstowcs-mbstowcsl"></a>mbstowcs, _mbstowcs_l

Konwertuje sekwencję znaków wielobajtowych do odpowiedniej sekwencji znaków dwubajtowych. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [mbstowcs_s —, _mbstowcs_s_l —](mbstowcs-s-mbstowcs-s-l.md).

## <a name="syntax"></a>Składnia

```C
size_t mbstowcs(
   wchar_t *wcstr,
   const char *mbstr,
   size_t count
);
size_t _mbstowcs_l(
   wchar_t *wcstr,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t mbstowcs(
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
size_t _mbstowcs_l(
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*wcstr*<br/>
Adres sekwencji znaków dwubajtowych.

*mbstr*<br/>
Adres sekwencji null zakończone znaków wielobajtowych.

*Liczba*<br/>
Maksymalna liczba znaków wielobajtowych do przekonwertowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Jeśli **mbstowcs** pomyślnie konwertuje ciąg źródłowy zwraca liczbę znaków wielobajtowych przekonwertowana. Jeśli *wcstr* argument jest **NULL**, funkcja zwraca wymagany rozmiar (w znaki dwubajtowe) ciągu docelowego. Jeśli **mbstowcs** napotka nieprawidłowy znak wielobajtowy, zwraca -1. Jeśli wartość zwracana jest *liczba*, ciąg znaków dwubajtowych nie jest zakończony znakiem null.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie zachodziły na siebie oraz że *liczba* poprawnie odzwierciedla liczbę znaków wielobajtowych do przekonwertowania.

## <a name="remarks"></a>Uwagi

**Mbstowcs** funkcja konwertuje aż maksymalnej liczby *liczba* znaki wielobajtowe wskazywany przez *mbstr* ciąg odpowiedniego szerokich znaków, które są ustalany na podstawie bieżących ustawień regionalnych. Przechowuje wynikowy ciąg znaków dwubajtowych pod adresem reprezentowany przez *wcstr*. Wynik jest podobny do serii wywołań [mbtowc](mbtowc-mbtowc-l.md). Jeśli **mbstowcs** napotka jednobajtowego znaku null (\0) przed lub po *liczba* problem wystąpi, konwertuje znak null do znaku null szerokich znaków (L '\0') i zatrzymuje. W związku z tym ciągiem znaku dwubajtowego *wcstr* jest zakończony znakiem null tylko wtedy, gdy występuje znak null podczas konwersji. Jeśli sekwencji wskazywany przez *wcstr* i *mbstr* nakładają się na siebie, zachowanie jest niezdefiniowane.

Jeśli *wcstr* argument jest **NULL**, **mbstowcs** zwraca liczbę znaków dwubajtowych, wynikających z konwersji, nie wliczając terminator o wartości null. Ciąg źródłowy musi być zakończony zerem do poprawnej wartości, które mają zostać zwrócone. Jeśli potrzebujesz wynikowy ciąg znaków dwubajtowych jako zakończony znakiem null, dodaj je do zwróconej wartości.

Jeśli *mbstr* argument jest **NULL**, lub jeśli *liczba* jest > **INT_MAX**, wywołany nieprawidłowy parametr uchwytu, zgodnie z opisem w [ Walidacja parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, numer błędu jest ustawiony na **EINVAL** a funkcja zwraca wartość -1.

**mbstowcs** używa bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych; **_mbstowcs_l —** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

W języku C++ funkcje te mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbstowcs**|\<stdlib.h>|
|**_mbstowcs_l**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_mbstowcs.c
// compile with: /W3
// illustrates the behavior of the mbstowcs function

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main( void )
{
    size_t size;
    int nChar = 2; // number of characters to convert
    int requiredSize;

    unsigned char    *pmbnull  = NULL;
    unsigned char    *pmbhello = NULL;
    char* localeInfo;

    wchar_t *pwchello = L"\x3042\x3043"; // 2 Hiragana characters
    wchar_t *pwc;

    /* Enable the Japanese locale and codepage */
    localeInfo = setlocale(LC_ALL, "Japanese_Japan.932");
    printf("Locale information set to %s\n", localeInfo);

    printf( "Convert to multibyte string:\n" );

    requiredSize = wcstombs( NULL, pwchello, 0); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s
    printf("   Required Size: %d\n", requiredSize);

    /* Add one to leave room for the null terminator. */
    pmbhello = (unsigned char *)malloc( requiredSize + 1);
    if (! pmbhello)
    {
        printf("Memory allocation failure.\n");
        return 1;
    }
    size = wcstombs( pmbhello, pwchello, requiredSize + 1); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s
    if (size == (size_t) (-1))
    {
        printf("Couldn't convert string. Code page 932 may"
                " not be available.\n");
        return 1;
    }
    printf( "   Number of bytes written to multibyte string: %u\n",
            (unsigned int) size );
    printf( "   Hex values of the" );
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );
    printf( "   Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");

    printf( "Convert back to wide-character string:\n" );

    /* Assume we don't know the length of the multibyte string.
     Get the required size in characters, and allocate enough space. */

    requiredSize = mbstowcs(NULL, pmbhello, 0); // C4996
    /* Add one to leave room for the null terminator */
    pwc = (wchar_t *)malloc( (requiredSize + 1) * sizeof( wchar_t ));
    if (! pwc)
    {
        printf("Memory allocation failure.\n");
        return 1;
    }
    size = mbstowcs( pwc, pmbhello, requiredSize + 1); // C4996
    if (size == (size_t) (-1))
    {
       printf("Couldn't convert string--invalid multibyte character.\n");
    }
    printf( "   Characters converted: %u\n", (unsigned int)size );
    printf( "   Hex value of first 2" );
    printf( " wide characters: %#.4x %#.4x\n\n", pwc[0], pwc[1] );
    free(pwc);
    free(pmbhello);
}
```

```Output
Locale information set to Japanese_Japan.932
Convert to multibyte string:
   Required Size: 4
   Number of bytes written to multibyte string: 4
   Hex values of the  multibyte characters: 0x82 0xa0 0x82 0xa1
   Codepage 932 uses 0x81 to 0x9f as lead bytes.

Convert back to wide-character string:
   Characters converted: 2
   Hex value of first 2 wide characters: 0x3042 0x3043
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>

---
title: mbstowcs, _mbstowcs_l
ms.date: 4/2/2020
api_name:
- mbstowcs
- _mbstowcs_l
- _o__mbstowcs_l
- _o_mbstowcs
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbstowcs
helpviewer_keywords:
- _mbstowcs_l function
- mbstowcs_l function
- mbstowcs function
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
ms.openlocfilehash: 11ff6920ea5f1dad2925a8010c9202e012fad87a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338847"
---
# <a name="mbstowcs-_mbstowcs_l"></a>mbstowcs, _mbstowcs_l

Konwertuje sekwencję znaków wielobajtowych na odpowiednią sekwencję znaków szerokich. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md).

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
Adres sekwencji szerokich znaków.

*mbstr*<br/>
Adres sekwencji znaków wielobajtowych zakończonych wartościami null.

*Liczba*<br/>
Maksymalna liczba znaków wielobajtowych do konwersji.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Jeśli **mbstowcs** pomyślnie konwertuje ciąg źródłowy, zwraca liczbę przekonwertowanych znaków wielobajtowych. Jeśli argument *wcstr* ma **wartość NULL**, funkcja zwraca wymagany rozmiar (w postaci szerokich) ciągu docelowego. Jeśli **mbstowcs** napotka nieprawidłowy znak wielobajtowy, zwraca wartość -1. Jeśli wartość zwracana jest *liczona,* ciąg szerokoznakowy nie jest zakończony zerem.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie nakładają się na siebie, a *liczba ta* poprawnie odzwierciedla liczbę znaków wielobajtowych do konwersji.

## <a name="remarks"></a>Uwagi

Funkcja **mbstowcs** konwertuje maksymalnie do *maksymalnej* liczby znaków wielobajtowych wskazywalonych przez *mbstr* na ciąg odpowiadających im znaków szerokich, które są określane przez bieżące ustawienia regionalne. Przechowuje wynikowy ciąg znaków szerokich pod adresem reprezentowanym przez *wcstr*. Wynik jest podobny do serii wywołań [mbtowc](mbtowc-mbtowc-l.md). Jeśli **mbstowcs** napotka pojedynczy znak null ('\0') przed lub po wystąpieniu *zliczania,* konwertuje znak null na znak null o szerokim znaku znaków (L'\0') i zatrzymuje. W związku z tym ciąg szerokoznakowy w *wcstr* jest zakończony zerem tylko wtedy, gdy znak null zostanie napotkany podczas konwersji. Jeśli sekwencje wskazane przez *wcstr* i *mbstr* nakładają się, zachowanie jest niezdefiniowane.

Jeśli argument *wcstr* ma **wartość NULL**, **mbstowcs** zwraca liczbę znaków szerokich, które mogłyby wynikać z konwersji, z wyłączeniem terminatora zerowego. Ciąg źródłowy musi być zakończony z wartością null, aby zwracana została poprawna wartość. Jeśli potrzebujesz wynikowego ciągu znaków szerokiego, który ma zostać zakończony zerem, dodaj jeden do zwracanych wartości.

Jeśli argument *mbstr* ma **wartość NULL**lub jeśli *liczba* jest > **INT_MAX,** wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [programie Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, errno jest ustawiona na **Wartość EINVAL** i funkcja zwraca -1.

**mbstowcs** używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; **_mbstowcs_l** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbstowcs**|\<>|
|**_mbstowcs_l**|\<>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[Multibytetowidechar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>

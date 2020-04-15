---
title: wcstombs, _wcstombs_l
ms.date: 4/2/2020
api_name:
- wcstombs
- _wcstombs_l
- _o__wcstombs_l
- _o_wcstombs
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcstombs
- _wcstombs_l
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
ms.openlocfilehash: fb95c6d73a3979a39995b9104a76fc42ca9e8535
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366721"
---
# <a name="wcstombs-_wcstombs_l"></a>wcstombs, _wcstombs_l

Konwertuje sekwencję znaków szerokich na odpowiednią sekwencję znaków wielobajtowych. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md).

## <a name="syntax"></a>Składnia

```C
size_t wcstombs(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count
);
size_t _wcstombs_l(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t wcstombs(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only
template <size_t size>
size_t _wcstombs_l(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbstr*<br/>
Adres sekwencji znaków wielobajtowych.

*wcstr*<br/>
Adres sekwencji szerokich znaków.

*Liczba*<br/>
Maksymalna liczba bajtów, które mogą być przechowywane w ciągu wyjściowym wielobajtowego.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Jeśli **wcstombs** pomyślnie konwertuje ciąg wielobajtowy, zwraca liczbę bajtów zapisanych w wielobajtowym ciągu wyjściowym, z wyłączeniem kończącej się wartości null (jeśli istnieje). Jeśli argument *mbstr* ma **wartość NULL**, **wcstombs** zwraca wymagany rozmiar w bajtach ciągu docelowego. Jeśli **wcstombs** napotka szeroki znak nie można przekonwertować na znak wielobajtowy, zwraca -1 oddanych do typu **size_t** i ustawia **errno** do **EILSEQ**.

## <a name="remarks"></a>Uwagi

Funkcja **wcstombs** konwertuje ciąg znaków szerokoznakowych wskazywalnych przez *wcstr* na odpowiednie znaki wielobajtowe i przechowuje wyniki w tablicy *mbstr.* Parametr *count* wskazuje maksymalną liczbę bajtów, które mogą być przechowywane w ciągu wyjściowym wielobajtowym (czyli rozmiar *mbstr*). Ogólnie nie wiadomo, ile bajtów będzie wymaganych podczas konwertowania ciągu znaków szerokoznakowych. Niektóre szerokie znaki będą wymagać tylko jednego bajtu w ciągu wyjściowym; inne wymagają dwóch. Jeśli istnieją dwa bajty w ciągu wyjściowym wielobajtów dla każdego szerokiego znaku w ciągu wejściowym (w tym szeroki znak null), wynik jest gwarantowane, aby dopasować.

Jeśli **wcstombs** napotka znak null o szerokim znaku (L'\0') przed lub po wystąpieniu *licznika,* konwertuje go na 8-bitowy 0 i zatrzymuje. W związku z tym ciąg znaków wielobajtowych w *mbstr* jest zakończony zerem tylko wtedy, **gdy wcstombs** napotka znak null o szerokim znaku podczas konwersji. Jeśli sekwencje wskazywały *przez wcstr* i *mbstr* pokrywają się, zachowanie **wcstombs** jest niezdefiniowane.

Jeśli argument *mbstr* ma **wartość NULL**, **wcstombs** zwraca wymagany rozmiar w bajtach ciągu docelowego.

**wcstombs** sprawdza jego parametry. Jeśli *wcstr* ma **wartość NULL**lub jeśli *liczba* jest większa niż **INT_MAX,** ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcja ustawia **errno** na **EINVAL** i zwraca -1.

**wcstombs** używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; **_wcstombs_l** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcstombs**|\<>|
|**_wcstombs_l**|\<>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program ilustruje zachowanie funkcji **wcstombs.**

```C
// crt_wcstombs.c
// compile with: /W3
// This example demonstrates the use
// of wcstombs, which converts a string
// of wide characters to a string of
// multibyte characters.

#include <stdlib.h>
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t  count;
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t *pWCBuffer = L"Hello, world.";

    printf("Convert wide-character string:\n" );

    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s instead
    printf("   Characters converted: %u\n",
            count );
    printf("    Multibyte character: %s\n\n",
           pMBBuffer );

    free(pMBBuffer);
}
```

```Output
Convert wide-character string:
   Characters converted: 13
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>

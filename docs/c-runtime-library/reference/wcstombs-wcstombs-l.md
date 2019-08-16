---
title: wcstombs, _wcstombs_l
ms.date: 11/04/2016
apiname:
- wcstombs
- _wcstombs_l
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
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: b5ee2a0e5636e9c1d1f3fc204b2b6cbf8b733d45
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498981"
---
# <a name="wcstombs-_wcstombs_l"></a>wcstombs, _wcstombs_l

Konwertuje sekwencję szerokich znaków do odpowiedniej sekwencji znaków wielobajtowych. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md).

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
Adres sekwencji znaków dwubajtowych.

*liczbą*<br/>
Maksymalna liczba bajtów, które mogą być przechowywane w ciągu znaków wielobajtowych.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Jeśli **wcstombs** pomyślnie konwertuje ciąg wielobajtowy, zwraca liczbę bajtów zapisanych do ciągu wyjściowego wielobajtowego, z wyłączeniem zakończenia null (jeśli istnieje). Jeśli argument *mbstr* ma **wartość null**, funkcja **wcstombs** zwraca wymagany rozmiar w bajtach ciągu docelowego. Jeśli **wcstombs** napotka znak dwubajtowy, nie może on zostać skonwertowany na znak wieloznaczny, zwraca-1 rzutowanie do typu **size_t** i ustawia **errno** na **EILSEQ**.

## <a name="remarks"></a>Uwagi

Funkcja **wcstombs** konwertuje ciąg znaków dwubajtowych wskazany przez *wcstr* na odpowiednie znaki wieloznaczne i zapisuje wyniki w tablicy *mbstr* . Parametr *Count* wskazuje maksymalną liczbę bajtów, które mogą być przechowywane w ciągu wyjściowym wielobajtowym (czyli rozmiarem *mbstr*). Ogólnie rzecz biorąc nie wiadomo, ile bajtów będzie wymaganych podczas konwertowania ciągu znaków dwubajtowych. Niektóre szerokie znaki będą wymagały tylko jednego bajtu w ciągu wyjściowym; inne wymagają dwóch. Jeśli istnieją dwa bajty w ciągu wyjściowym wielobajtowym dla każdego znaku dwuznacznego w ciągu wejściowym (w tym o szerokim znaku null), wynik jest zagwarantowany do dopasowania.

Jeśli **wcstombs** napotka znak dwubajtowy o wartości null (L ' \ 0 ') przed lub w przypadku występowania, konwertuje go na 8-bitowy 0 i zatrzyma. W ten sposób ciąg znaków wielobajtowych w *mbstr* jest zakończony wartością null tylko wtedy, gdy **wcstombs** napotka znak dwubajtowy o wartości null podczas konwersji. Jeśli sekwencje wskazywane przez *wcstr* i *mbstr* nakładają się na siebie, zachowanie **wcstombs** jest niezdefiniowane.

Jeśli argument *mbstr* ma **wartość null**, funkcja **wcstombs** zwraca wymagany rozmiar w bajtach ciągu docelowego.

**wcstombs** sprawdza poprawność swoich parametrów. Jeśli *wcstr* ma **wartość null**lub *Liczba* jest większa niż **INT_MAX**, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcja ustawia **errno** na **EINVAL** i zwraca wartość-1.

**wcstombs** używa bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych; **_wcstombs_l** jest identyczny, z tą różnicą, że w zamian korzysta z przekazaną ustawieniami regionalnymi. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W C++programie te funkcje mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program ilustruje zachowanie funkcji **wcstombs** .

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

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>

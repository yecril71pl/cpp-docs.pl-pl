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
ms.openlocfilehash: d102cd74061faeb0c41823e6cf5c9a8ef335294f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188587"
---
# <a name="wcstombs-wcstombsl"></a>wcstombs, _wcstombs_l

Konwertuje sekwencję znaków dwubajtowych do odpowiedniej sekwencji znaków wielobajtowych. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [wcstombs_s —, _wcstombs_s_l —](wcstombs-s-wcstombs-s-l.md).

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

*Liczba*<br/>
Maksymalna liczba bajtów, które mogą być przechowywane w ciągu znaków wielobajtowych danych wyjściowych.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Jeśli **wcstombs —** pomyślnie konwertuje ciąg wielobajtowy zwraca liczba bajtów zapisanych w ciągu wyjściowym wielobajtowego, z wyłączeniem zakończenia o wartości null (jeśli istnieje). Jeśli *mbstr* argument jest **NULL**, **wcstombs —** zwraca wymagany rozmiar w bajtach ciągu docelowego. Jeśli **wcstombs —** napotka znakiem dwubajtowym, nie można przekonwertować do znaku wielobajtowego, zwraca -1 rzutowane na typ **size_t** i ustawia **errno** do **EILSEQ** .

## <a name="remarks"></a>Uwagi

**Wcstombs —** funkcji konwertuje ciąg znaków dwubajtowych, wskazywana przez *wcstr* do odpowiedniego znaków wielobajtowych znaków i zapisuje wyniki w *mbstr* tablicy. *Liczba* parametr wskazuje maksymalną liczbę bajtów, które mogą być przechowywane w ciągu wyjściowym wielobajtowych (czyli rozmiar *mbstr*). Ogólnie rzecz biorąc nie wiadomo, ile bajtów będzie wymagane podczas konwertowania ciągu znaków dwubajtowych. Niektóre znaki dwubajtowe będzie wymagać tylko jednego bajtu w ciągu wyjściowym; inne wymagają dwóch. W przypadku dwóch bajtów w ciąg znaków wielobajtowych dane wyjściowe dla każdego znaku dwubajtowego ciągu wejściowego (w tym znakiem dwubajtowym o wartości null), wynik jest gwarantowane.

Jeśli **wcstombs —** napotka znaków dwubajtowych znakiem null (L '\0'), przed lub po *liczba* występuje i konwertuje ją do 8-bitową 0 i kończy działanie. W związku z tym ciągu znaków wielobajtowych *mbstr* jest zakończony znakiem null tylko wtedy, gdy **wcstombs —** napotka znaku dwubajtowego znaku null podczas konwersji. Jeśli sekwencji wskazywany przez *wcstr* i *mbstr* zachodziły na siebie, zachowanie **wcstombs —** jest niezdefiniowana.

Jeśli *mbstr* argument jest **NULL**, **wcstombs —** zwraca wymagany rozmiar w bajtach ciągu docelowego.

**wcstombs —** sprawdza poprawność parametrów. Jeśli *wcstr* jest **NULL**, lub jeśli *liczba* jest większa niż **INT_MAX**, funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcja ustawia **errno** do **EINVAL** i zwraca wartość -1.

**wcstombs —** używa bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych; **_wcstombs_l —** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

W języku C++ funkcje te mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcstombs —**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program ilustruje zachowanie **wcstombs —** funkcji.

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
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>

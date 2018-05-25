---
title: wcstombs —, _wcstombs_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- wcstombs
- _wcstombs_l
dev_langs:
- C++
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 604ca2d2172e340459d7d5cbf406f01c484750ff
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="wcstombs-wcstombsl"></a>wcstombs, _wcstombs_l

Konwertuje odpowiedniej sekwencji znaków wielobajtowych sekwencji znaki dwubajtowe. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [wcstombs_s —, _wcstombs_s_l —](wcstombs-s-wcstombs-s-l.md).

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
Adres sekwencję znaki dwubajtowe.

*Liczba*<br/>
Maksymalna liczba bajtów, które mogą być przechowywane w ciągu znaków wielobajtowych danych wyjściowych.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Jeśli **wcstombs —** pomyślnie konwertuje ciąg znaków wielobajtowych, zwraca liczbę bajtów zapisanych w ciągu wielobajtowe dane wyjściowe, bez przerywania null (jeśli istnieje). Jeśli *mbstr* argument jest **NULL**, **wcstombs —** zwraca wymagany rozmiar w bajtach ciągu docelowego. Jeśli **wcstombs —** napotka znaków dwubajtowych nie można przekonwertować znaków wielobajtowych, zwraca -1 rzutowany na typ **size_t** i ustawia **errno** do **eilseq —** .

## <a name="remarks"></a>Uwagi

**Wcstombs —** funkcja konwertuje ciąg znaków dwubajtowych wskazywana przez *wcstr* do odpowiedniego wielobajtowych znaków i przechowuje wyniki w *mbstr* tablicy. *Liczba* parametr wskazuje maksymalną liczbę bajtów, które mogą być przechowywane w ciągu wyjściowego Wielobajtowe (to znaczy, że rozmiar *mbstr*). Ogólnie rzecz biorąc nie wiadomo, ile bajty będzie wymagane podczas konwertowania ciągu znaków dwubajtowych. Niektóre znaki dwubajtowe wymaga tylko jednego bajtu w ciągu wyjściowego; inne wymagają dwa. Jeśli istnieją dwa bajty w ciągu wielobajtowe danych wyjściowych dla każdego znaku dwubajtowego w ciągu wejściowym (w tym znaków typu wide null), wynik jest gwarancji.

Jeśli **wcstombs —** napotka znak null znaków dwubajtowych (L '\0'), przed lub po *liczba* występuje i konwertuje ją na 8-bitowej 0 i powoduje zatrzymanie. W związku z tym ciąg znaków wielobajtowych *mbstr* jest zakończony wartością null tylko wtedy, gdy **wcstombs —** napotka znak null znaków dwubajtowych podczas konwersji. Jeśli sekwencje wskazywana przez *wcstr* i *mbstr* nakładają się zachowanie **wcstombs —** jest niezdefiniowana.

Jeśli *mbstr* argument jest **NULL**, **wcstombs —** zwraca wymagany rozmiar w bajtach ciągu docelowego.

**wcstombs —** sprawdza poprawność parametrów. Jeśli *wcstr* jest **NULL**, lub jeśli *liczba* jest większa niż **int_max —**, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może kontynuować, funkcja ustawia **errno** do **einval —** i zwraca wartość -1.

**wcstombs —** używa bieżące ustawienia regionalne dla dowolnego zachowań zależnych od ustawień regionalnych. **_wcstombs_l —** jest identyczny z tą różnicą, że używa ustawień regionalnych przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują odpowiedników nowsza, bezpieczne tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcstombs —**|\<stdlib.h>|
|**_wcstombs_l —**|\<stdlib.h>|

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
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)<br/>

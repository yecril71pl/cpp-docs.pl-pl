---
title: wctob
ms.date: 11/04/2016
api_name:
- wctob
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctob
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
ms.openlocfilehash: 151325b0d66e6d57156cdf94828ca1d4b151d437
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944930"
---
# <a name="wctob"></a>wctob

Określa, czy znak dwubajtowy odnosi się do znaku wieloznacznego i zwraca reprezentację znaku wielobajtowego.

## <a name="syntax"></a>Składnia

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>Parametry

*WCHAR*<br/>
Wartość do przetłumaczenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli **wctob** pomyślnie konwertuje znak dwubajtowy, zwraca swoją reprezentację znaku wieloznacznego, tylko wtedy, gdy znak wielobajtowy ma dokładnie jeden bajt Long. Jeśli **wctob** napotka znak dwubajtowy, nie może on zostać skonwertowany na znak wieloznaczny lub znak wielobajtowy nie jest dokładnie jednobajtowy, zwraca wartość-1.

## <a name="remarks"></a>Uwagi

Funkcja **wctob** konwertuje szeroką literę zawartą w *WCHAR* do odpowiedniego znaku wielobajtowego przekazaną przez zwracaną wartość **int** , jeśli znak wielobajtowy ma dokładnie jeden bajt Long.

Jeśli **wctob** zakończyło się niepowodzeniem i nie znaleziono odpowiedniego znaku wielobajtowego, funkcja ustawia **errno** na **EILSEQ** i zwraca wartość-1.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wctob**|\<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program ilustruje zachowanie funkcji **wcstombs** .

```C
// crt_wctob.c
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    int     bChar = 0;
    wint_t  wChar = 0;

    // Set the corresponding wide character to exactly one byte.
    wChar = (wint_t)'A';

    bChar = wctob( wChar );
    if (bChar == WEOF)
    {
        printf( "No corresponding multibyte character was found.\n");
    }
    else
    {
        printf( "Determined the corresponding multibyte character to"
                " be \"%c\".\n", bChar);
    }
}
```

```Output
Determined the corresponding multibyte character to be "A".
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>

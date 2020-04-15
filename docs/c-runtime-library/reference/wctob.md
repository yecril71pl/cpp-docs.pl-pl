---
title: wctob
ms.date: 4/2/2020
api_name:
- wctob
- _o_wctob
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 420071680c3dc273f6df637cf44273f2c24bd64c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320445"
---
# <a name="wctob"></a>wctob

Określa, czy szeroki znak odpowiada znakowi wielobajtowego i zwraca jego reprezentację wielobajtowych znaków.

## <a name="syntax"></a>Składnia

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>Parametry

*Wchar*<br/>
Wartość do przetłumaczenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli **wctob** pomyślnie konwertuje szeroki znak, zwraca jego wielobajtową reprezentację znaków, tylko wtedy, gdy znak wielobajtowy ma dokładnie jeden bajt. Jeśli **wctob** napotka szeroki znak, nie może przekonwertować na znak wielobajtowy lub znak wielobajtowy nie jest dokładnie jeden bajt długo, zwraca -1.

## <a name="remarks"></a>Uwagi

Funkcja **wctob** konwertuje szeroki znak zawarty w *wchar* na odpowiedni znak wielobajtowy przekazywany przez zwracaną wartość **int,** jeśli znak wielobajtowy ma dokładnie jeden bajt.

Jeśli **wctob** nie powiodło się i nie znaleziono odpowiedniego znaku wielobajtowego, funkcja ustawia **errno** na **EILSEQ** i zwraca -1.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program ilustruje zachowanie funkcji **wcstombs.**

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

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>

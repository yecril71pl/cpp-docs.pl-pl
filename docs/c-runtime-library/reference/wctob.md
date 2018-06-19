---
title: wctob — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wctob
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
- wctob
dev_langs:
- C++
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1cff2dcb8d6b0ad3756a8a0047fcc9b982fb7bb8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411448"
---
# <a name="wctob"></a>wctob

Określa, czy znaków dwubajtowych odpowiada znaków wielobajtowych i zwraca jego reprezentacja znaków wielobajtowych.

## <a name="syntax"></a>Składnia

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>Parametry

*WChar*<br/>
Wartość do tłumaczenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli **wctob —** pomyślnie konwertuje znaków dwubajtowych, zwraca jej reprezentacji znaków wielobajtowych tylko wtedy, gdy znaków wielobajtowych dokładnie jednego bajtu. Jeśli **wctob —** napotka znaków dwubajtowych nie można konwertować znaków wielobajtowych lub znaków wielobajtowych nie jest dokładnie jeden długi, zwraca -1 bajt.

## <a name="remarks"></a>Uwagi

**Wctob —** funkcja konwertuje znaków dwubajtowych zawarte w *wchar* do odpowiednich znaków wielobajtowych przekazany przez zwracany **int** wartość, jeśli wielobajtowe znak jest dokładnie jeden bajt.

Jeśli **wctob —** nie powiodła się i nie odpowiednich znaków wielobajtowych znaleziono funkcja ustawia **errno** do **eilseq —** i zwraca wartość -1.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wctob**|\<WChar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program ilustruje zachowanie **wcstombs —** funkcji.

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
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)<br/>

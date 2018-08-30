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
ms.openlocfilehash: 61d92c02c4410bdc01b76ac6307fb9bb2652880a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203611"
---
# <a name="wctob"></a>wctob

Określa, jeśli znak dwubajtowy odnosi się do znaków wielobajtowych i zwraca jego reprezentację w postaci znaku wielobajtowego.

## <a name="syntax"></a>Składnia

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>Parametry

*WChar*<br/>
Wartość do translacji.

## <a name="return-value"></a>Wartość zwracana

Jeśli **wctob —** pomyślnie konwertuje znakiem dwubajtowym tylko wtedy, gdy znak wielobajtowy jest dokładnie jeden bajt zwraca jej reprezentacji znaków wielobajtowych. Jeśli **wctob —** napotka znakiem dwubajtowym, nie można przekonwertować na znak wielobajtowy lub znak wielobajtowy nie jest dokładnie jeden bajt, zwraca -1.

## <a name="remarks"></a>Uwagi

**Wctob —** funkcja konwertuje znakiem dwubajtowym zawarte w *wchar* do odpowiedniego znaku wielobajtowego przekazywane przez zwracany **int** wartość, jeśli znaków wielobajtowych znak jest dokładnie jednego bajtu.

Jeśli **wctob —** nie powiodło się, a nie znaleziono żadnych odpowiedniego znaku wielobajtowego, funkcja ustawia **errno** do **EILSEQ** i zwraca wartość -1.

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
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>

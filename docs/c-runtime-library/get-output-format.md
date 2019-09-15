---
title: _get_output_format
ms.date: 11/04/2016
api_name:
- _get_output_format
api_location:
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_output_format
- _get_output_format
helpviewer_keywords:
- output formatting
- get_output_format function
- _get_output_format function
ms.assetid: 0ce42f3b-3479-41c4-bcbf-1d21f7ee37e7
ms.openlocfilehash: 20afa988bc4fdf3bc3a6ff073a48a1cc00ff84c5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944366"
---
# <a name="_get_output_format"></a>_get_output_format

Pobiera bieżącą wartość flagi formatu danych wyjściowych.

> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest on dostępny w CRT.

## <a name="syntax"></a>Składnia

```
unsigned int _get_output_format();
```

## <a name="return-value"></a>Wartość zwracana

Bieżąca wartość flagi formatu danych wyjściowych.

## <a name="remarks"></a>Uwagi

Flaga formatu danych wyjściowych kontroluje funkcje sformatowanych operacji we/wy. W obecnym przypadku flaga ma dwie możliwe wartości: 0 i `_TWO_DIGIT_EXPONENT`. Jeśli `_TWO_DIGIT_EXPONENT` jest ustawiona, liczby zmiennoprzecinkowe są drukowane z tylko dwiema cyframi w wykładniku, chyba że trzecia cyfra jest wymagana przez rozmiar wykładnika. Jeśli flaga ma wartość zero, zmiennoprzecinkowe dane wyjściowe wyświetlają trzy cyfry wykładnika, w razie potrzeby w celu uzupełnienia wartości do trzech cyfr.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_get_output_format`|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz temat [zgodność](../c-runtime-library/compatibility.md) we wprowadzeniu.

## <a name="see-also"></a>Zobacz także

[Składnia specyfikacji formatu: funkcje printf i wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_set_output_format](../c-runtime-library/set-output-format.md)

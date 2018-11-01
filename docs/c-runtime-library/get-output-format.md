---
title: _get_output_format
ms.date: 11/04/2016
apiname:
- _get_output_format
apilocation:
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- get_output_format
- _get_output_format
helpviewer_keywords:
- output formatting
- get_output_format function
- _get_output_format function
ms.assetid: 0ce42f3b-3479-41c4-bcbf-1d21f7ee37e7
ms.openlocfilehash: a78ffb1c7fd32db3092bcf1d2297a0be6fa9f47b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518798"
---
# <a name="getoutputformat"></a>_get_output_format

Pobiera bieżącą wartość flagi formatu danych wyjściowych.

> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.

## <a name="syntax"></a>Składnia

```
unsigned int _get_output_format();
```

## <a name="return-value"></a>Wartość zwracana

Bieżąca wartość flagi formatu danych wyjściowych.

## <a name="remarks"></a>Uwagi

Flagi formatu danych wyjściowych steruje funkcjami sformatowane we/wy. Obecnie flaga nie wywiera dwóch wartości: 0 i `_TWO_DIGIT_EXPONENT`. Jeśli `_TWO_DIGIT_EXPONENT` ustawiono wartość zmiennoprzecinkowa liczb zmiennoprzecinkowych zostanie wydrukowany tylko dwie cyfry wykładnika, chyba że trzecia cyfra jest wymagana przez rozmiar wykładnik potęgi. Jeśli flaga wynosi zero, dane wyjściowe zmiennoprzecinkowych, wyświetla trzy cyfry wykładnika, za pomocą zera, jeśli jest to niezbędne do wypełnienia wartości do trzech cyfr.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_get_output_format`|\<stdio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md) we wstępie.

## <a name="see-also"></a>Zobacz też

[Składnia specyfikacji formatu: funkcje printf i wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_set_output_format](../c-runtime-library/set-output-format.md)

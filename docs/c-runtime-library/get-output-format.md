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
ms.openlocfilehash: 682ab9796942e52ed036193887158ea22b738189
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349340"
---
# <a name="_get_output_format"></a>_get_output_format

Pobiera bieżącą wartość flagi formatu wyjściowego.

> [!IMPORTANT]
> Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.

## <a name="syntax"></a>Składnia

```
unsigned int _get_output_format();
```

## <a name="return-value"></a>Wartość zwracana

Bieżąca wartość flagi formatu wyjściowego.

## <a name="remarks"></a>Uwagi

Flaga formatu wyjściowego steruje funkcjami sformatowanych operacji we/wy. Obecnie flaga ma dwie możliwe wartości: 0 i `_TWO_DIGIT_EXPONENT`. Jeśli `_TWO_DIGIT_EXPONENT` jest ustawiona, liczby zmiennoprzecinkowe są drukowane tylko z dwiema cyframi w wykładniku, chyba że trzecia cyfra jest wymagana przez rozmiar wykładnika. Jeśli flaga wynosi zero, dane wyjściowe zmiennoprzecinkowe wyświetla trzy cyfry wykładnika, używając zer, jeśli to konieczne, aby przekazać wartość do trzech cyfr.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_get_output_format`|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../c-runtime-library/compatibility.md) we wstępie.

## <a name="see-also"></a>Zobacz też

[Składnia specyfikacji formatu: printf i wprintf Functions](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_set_output_format](../c-runtime-library/set-output-format.md)

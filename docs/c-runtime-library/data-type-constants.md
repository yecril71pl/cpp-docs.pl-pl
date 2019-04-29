---
title: Typ danych — Stałe
ms.date: 06/25/2018
f1_keywords:
- FLT_MIN
- SHRT_MAX
- CHAR_MIN
- MB_LEN_MAX
- DBL_EPSILON
- SHRT_MIN
- _FLT_RADIX
- FLT_DIG
- FLT_MAX_10_EXP
- FLT_MANT_DIG
- DBL_MAX_EXP
- SCHAR_MIN
- SCHAR_MAX
- DBL_MIN
- FLT_MIN_10_EXP
- _DBL_ROUNDS
- USHRT_MAX
- FLT_MAX_EXP
- LONG_MAX
- DBL_MAX
- DBL_DIG
- FLT_MIN_EXP
- INT_MIN
- DBL_MIN_10_EXP
- CHAR_BIT
- INT_MAX
- ULONG_MAX
- DBL_MIN_EXP
- LONG_MIN
- _FLT_ROUNDS
- DBL_MANT_DIG
- _DBL_RADIX
- CHAR_MAX
- FLT_MAX
- DBL_MAX_10_EXP
- UCHAR_MAX
- FLT_EPSILON
- UINT_MAX
- LLONG_MIN
- LLONG_MAX
- ULLONG_MAX
- _I8_MIN
- _I8_MAX
- _UI8_MAX
- _I16_MIN
- _I16_MAX
- _UI16_MAX
- _I32_MIN
- _I32_MAX
- _UI32_MAX
- _I64_MIN
- _I64_MAX
- _UI64_MAX
- _I128_MIN
- _I128_MAX
- _UI128_MAX
- SIZE_MAX
- RSIZE_MAX
- LDBL_DIG
- LDBL_EPSILON
- LDBL_HAS_SUBNORM
- LDBL_MANT_DIG
- LDBL_MAX
- LDBL_MAX_10_EXP
- LDBL_MAX_EXP
- LDBL_MIN
- LDBL_MIN_10_EXP
- LDBL_MIN_EXP
- _LDBL_RADIX
- LDBL_TRUE_MIN
- DECIMAL_DIG
helpviewer_keywords:
- DBL_MAX_EXP constant
- _DBL_RADIX constant
- FLT_MIN_EXP constant
- DBL_EPSILON constant
- INT_MIN constant
- FLT_EPSILON constant
- DBL_MANT_DIG constant
- _FLT_RADIX constant
- DBL_MIN constant
- USHRT_MAX constant
- FLT_MAX_10_EXP constant
- _FLT_ROUNDS constant
- data type constants [C++]
- _DBL_ROUNDS constant
- CHAR_MAX constant
- FLT_MAX_EXP constant
- FLT_MIN constant
- CHAR_MIN constant
- FLT_MIN_10_EXP constant
- DBL_MIN_EXP constant
- SCHAR_MAX constant
- FLT_RADIX constant
- CHAR_BIT constant
- UCHAR_MAX constant
- DBL_RADIX constant
- FLT_ROUNDS constant
- LONG_MIN constant
- SHRT_MAX constant
- LONG_MAX constant
- DBL_MAX_10_EXP constant
- DBL_MIN_10_EXP constant
- INT_MAX constant
- constants [C++], data type
- ULONG_MAX constant
- FLT_DIG constant
- MB_LEN_MAX constant
- DBL_DIG constant
- SHRT_MIN constant
- DBL_MAX constant
- DBL_ROUNDS constant
- FLT_MAX constant
- UINT_MAX constant
- FLT_MANT_DIG constant
- SCHAR_MIN constant
- LLONG_MIN constant
- LLONG_MAX constant
- ULLONG_MAX constant
- _I8_MIN constant
- _I8_MAX constant
- _UI8_MAX constant
- _I16_MIN constant
- _I16_MAX constant
- _UI16_MAX constant
- _I32_MIN constant
- _I32_MAX constant
- _UI32_MAX constant
- _I64_MIN constant
- _I64_MAX constant
- _UI64_MAX constant
- _I128_MIN constant
- _I128_MAX constant
- _UI128_MAX constant
- SIZE_MAX constant
- RSIZE_MAX constant
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
ms.openlocfilehash: c4ffbf294083131f29ffe957fd0434182fbb8f99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344398"
---
# <a name="data-type-constants"></a>Typ danych — Stałe

Typ danych — stałe są zakresy zależne od implementacji wartości dozwolone w przypadku typów całkowitych i zmiennoprzecinkowych danych.

## <a name="integral-type-constants"></a>Stałe typu całkowitego

Te stałe oferują zakresy dla typów całkowitych danych. Aby użyć tych stałych, należy dołączyć nagłówek limits.h w pliku źródłowym:

```C
#include <limits.h>
```

> [!NOTE]
> [/J.](../build/reference/j-default-char-type-is-unsigned.md) — opcja kompilatora zmienia domyślny **char** typ **niepodpisane**.

|Stała|Wartość|Opis|
|--------------|-----------|-------------|
|**CHAR_BIT**|8|Liczba bitów **char**|
|**SCHAR_MIN**|(-128)|Co najmniej podpisany **char** wartość|
|**SCHAR_MAX**|127|Maksymalna podpisany **char** wartość|
|**UCHAR_MAX**|255 (0xff)|Maksymalna **niepodpisane** **char** wartość|
|**CHAR_MIN**|(od -128) (0, jeśli **/j.** opcja używana)|Co najmniej **char** wartość|
|**CHAR_MAX**|127 (jeśli 255 **/j.** opcja używana)|Maksymalna **char** wartość|
|**MB_LEN_MAX**|5|Maksymalna liczba bajtów znaków wielobajtowych **char**|
|**SHRT_MIN**|-32768|Co najmniej podpisany **krótki** wartość|
|**SHRT_MAX**|32767|Maksymalna podpisany **krótki** wartość|
|**USHRT_MAX**|65535 (0xffff)|Maksymalna **niepodpisane** **krótki** wartość|
|**INT_MIN**|(-2147483647 - 1)|Co najmniej podpisany **int** wartość|
|**INT_MAX**|2147483647|Maksymalna podpisany **int** wartość|
|**UINT_MAX**|4294967295 (0xffffffff)|Maksymalna **niepodpisane** **int** wartość|
|**LONG_MIN**|(-2147483647 L - 1)|Co najmniej podpisany **długie** wartość|
|**LONG_MAX**|2147483647L|Maksymalna podpisany **długie** wartość|
|**ULONG_MAX**|4294967295UL (0xfffffffful)|Maksymalna **niepodpisane** **długie** wartość|
|**LLONG_MIN**|(- 9223372036854775807LL - 1)|Co najmniej podpisany **długie** **długie** lub **__int64** wartość|
|**LLONG_MAX**|9223372036854775807LL|Maksymalna podpisany **długie** **długie** lub **__int64** wartość|
|**ULLONG_MAX**|0xffffffffffffffffull|Maksymalna **niepodpisane** **długie** **długie** wartość|
|**_I8_MIN**|(- 127i8 - 1)|Co najmniej podpisany 8-bitową wartością|
|**_I8_MAX**|127i8|Maksymalna podpisany 8-bitową wartością|
|**_UI8_MAX**|0xffui8|Wartość maksymalna 8-bitowych unsigned|
|**_I16_MIN**|(- 32767i16 - 1)|Co najmniej podpisany 16-bitową wartość|
|**_I16_MAX**|32767i16|Maksymalna podpisany 16-bitową wartość|
|**_UI16_MAX**|0xffffui16|Maksymalna wartość 16-bitowych unsigned|
|**_I32_MIN**|(- 2147483647i32 - 1)|Co najmniej podpisany 32-bitową wartość|
|**_I32_MAX**|2147483647i32|Maksymalna podpisany 32-bitową wartość|
|**_UI32_MAX**|0xffffffffui32|Maksymalna wartość 32-bitowych unsigned|
|**_I64_MIN**|(-9223372036854775807 - 1)|Co najmniej podpisany wartość 64-bitowa|
|**_I64_MAX**|9223372036854775807|Maksymalna podpisany wartość 64-bitowa|
|**_UI64_MAX**|0xffffffffffffffffui64|Maksymalna wartość 64-bitowych unsigned|
|**_I128_MIN**|(- 170141183460469231731687303715884105727i128 - 1)|Co najmniej podpisany 128-bitowej wartości|
|**_I128_MAX**|170141183460469231731687303715884105727i128|Maksymalna podpisany 128-bitowej wartości|
|**_UI128_MAX**|0xffffffffffffffffffffffffffffffffui128|Maksymalna wartość 128-bitowych unsigned|
|**SIZE_MAX**|taki sam jak **_UI64_MAX** Jeśli **_WIN64** jest zdefiniowany, lub **UINT_MAX**|Maksymalna liczba całkowita natywnych rozmiar|
|**RSIZE_MAX**|taki sam jak (**SIZE_MAX** >> 1)|Maksymalna bezpieczna biblioteka liczba całkowita określająca rozmiar|

## <a name="floating-point-type-constants"></a>Stałe typu zmiennoprzecinkowego

Nadaj następujących stałych, zakresu i inne cechy charakterystyczne **długie** **double**, **double** i **float** typy danych. Aby użyć tych stałych, należy dołączyć nagłówek float.h w pliku źródłowym:

```C
#include <float.h>
```

|Stała|Wartość|Opis|
|--------------|-----------|-----------------|
|**DBL_DECIMAL_DIG**|17|Liczba cyfr dziesiętnych zaokrąglania dokładności|
|**DBL_DIG**|15|Liczba cyfr dziesiętnych|
|**DBL_EPSILON**|2.2204460492503131e-016|Najmniejsza taki sposób, że 1.0 + **DBL_EPSILON** ! = 1,0|
|**DBL_HAS_SUBNORM**|1|Obsługuje typ subnormal (numery zdenormalizowany)|
|**DBL_MANT_DIG**|53|Liczba bitów mantysę (mantysy)|
|**DBL_MAX**|1, 7976931348623158e + 308.|Wartość maksymalna|
|**DBL_MAX_10_EXP**|308|Maksymalna wykładnik dziesiętna|
|**DBL_MAX_EXP**|1024|Maksymalna wykładnik binarne|
|**DBL_MIN**|2.2250738585072014e-308|Minimalna liczba znormalizowanych wartość dodatnią|
|**DBL_MIN_10_EXP**|(-307)|Minimalna wykładnik dziesiętna|
|**DBL_MIN_EXP**|(-1021)|Minimalna wykładnik binarne|
|**_DBL_RADIX**|2|Podstawy wykładnika|
|**DBL_TRUE_MIN**|4.9406564584124654e-324|Minimalna wartość subnormal dodatnią|
|**FLT_DECIMAL_DIG**|9|Liczba cyfr dziesiętnych zaokrąglania dokładności|
|**FLT_DIG**|6|Liczba cyfr dziesiętnych dokładności|
|**FLT_EPSILON**|1.192092896e-07F|Najmniejsza taki sposób, że 1.0 + **FLT_EPSILON** ! = 1,0|
|**FLT_HAS_SUBNORM**|1|Obsługuje typ subnormal (numery zdenormalizowany)|
|**FLT_MANT_DIG**|24|Liczba bitów mantysę (mantysy)|
|**FLT_MAX**|3.402823466e+38F|Wartość maksymalna|
|**FLT_MAX_10_EXP**|38|Maksymalna wykładnik dziesiętna|
|**FLT_MAX_EXP**|128|Maksymalna wykładnik binarne|
|**FLT_MIN**|1.175494351e-38F|Minimalna liczba znormalizowanych wartość dodatnią|
|**FLT_MIN_10_EXP**|(-37)|Minimalna wykładnik dziesiętna|
|**FLT_MIN_EXP**|(-125)|Minimalna wykładnik binarne|
|**FLT_RADIX**|2|Podstawy wykładnika|
|**FLT_TRUE_MIN**|1.401298464e-45F|Minimalna wartość subnormal dodatnią|
|**LDBL_DIG**|15|Liczba cyfr dziesiętnych|
|**LDBL_EPSILON**|2.2204460492503131e-016|Najmniejsza taki sposób, że 1.0 + **LDBL_EPSILON** ! = 1,0|
|**LDBL_HAS_SUBNORM**|1|Obsługuje typ subnormal (numery zdenormalizowany)|
|**LDBL_MANT_DIG**|53|Liczba bitów mantysę (mantysy)|
|**LDBL_MAX**|1, 7976931348623158e + 308.|Wartość maksymalna|
|**LDBL_MAX_10_EXP**|308|Maksymalna wykładnik dziesiętna|
|**LDBL_MAX_EXP**|1024|Maksymalna wykładnik binarne|
|**LDBL_MIN**|2.2250738585072014e-308|Minimalna liczba znormalizowanych wartość dodatnią|
|**LDBL_MIN_10_EXP**|(-307)|Minimalna wykładnik dziesiętna|
|**LDBL_MIN_EXP**|(-1021)|Minimalna wykładnik binarne|
|**_LDBL_RADIX**|2|Podstawy wykładnika|
|**LDBL_TRUE_MIN**|4.9406564584124654e-324|Minimalna wartość subnormal dodatnią|
|**DECIMAL_DIG**|taki sam jak **DBL_DECIMAL_DIG**|Domyślne (podwójny) cyfr dziesiętnych zaokrąglania dokładności|

## <a name="see-also"></a>Zobacz także

[Stałe globalne](../c-runtime-library/global-constants.md)

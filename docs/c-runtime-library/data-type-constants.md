---
title: Stałe typu danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55690bc06ae838ad44e1d0d6f0527974b7859b94
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952469"
---
# <a name="data-type-constants"></a>Typ danych — Stałe

Stałe typu danych są zależne od implementacji zakresów wartości dozwolone w przypadku typów całkowitych i zmiennoprzecinkowych danych.

## <a name="integral-type-constants"></a>Stałe typu całkowitego

Te stałe podać zakresy na typy całkowite danych. Aby korzystać z tych stałe, Dołącz nagłówek Limits.h — w pliku źródłowego:

```C
#include <limits.h>
```

> [!NOTE]
> [/J](../build/reference/j-default-char-type-is-unsigned.md) — opcja kompilatora zmienia domyślne **char** typ **niepodpisane**.

|Stała|Wartość|Opis|
|--------------|-----------|-------------|
|**CHAR_BIT**|8|Liczba bitów **char**|
|**SCHAR_MIN**|(-128)|Co najmniej podpisany **char** wartość|
|**SCHAR_MAX**|127|Maksymalna podpisany **char** wartość|
|**UCHAR_MAX**|255 (0xff)|Maksymalna **niepodpisane** **char** wartość|
|**CHAR_MIN —**|(-128) (Jeśli 0 **/J** opcja używana)|Co najmniej **char** wartość|
|**CHAR_MAX**|127 (jeśli 255 **/J** opcja używana)|Maksymalna **char** wartość|
|**MB_LEN_MAX**|5|Maksymalna liczba bajtów w wielobajtowe **char**|
|**SHRT_MIN**|-32768|Co najmniej podpisany **krótki** wartość|
|**SHRT_MAX**|32767|Maksymalna podpisany **krótki** wartość|
|**USHRT_MAX**|65535 (0xffff)|Maksymalna **niepodpisane** **krótki** wartość|
|**INT_MIN**|(-2147483647 - 1)|Co najmniej podpisany **int** wartość|
|**INT_MAX**|2147483647|Maksymalna podpisany **int** wartość|
|**UINT_MAX**|4294967295 (0xffffffff)|Maksymalna **niepodpisane** **int** wartość|
|**LONG_MIN —**|(-2147483647 L - 1)|Co najmniej podpisany **długi** wartość|
|**LONG_MAX**|2147483647L|Maksymalna podpisany **długi** wartość|
|**ULONG_MAX**|4294967295UL (0xfffffffful)|Maksymalna **niepodpisane** **długi** wartość|
|**LLONG_MIN**|(- 9223372036854775807LL - 1)|Co najmniej podpisany **długi** **długi** lub **__int64** wartości|
|**LLONG_MAX**|9223372036854775807LL|Maksymalna podpisany **długi** **długi** lub **__int64** wartości|
|**ULLONG_MAX**|0xffffffffffffffffull|Maksymalna **niepodpisane** **długi** **długi** wartość|
|**_I8_MIN**|(- 127i8 - 1)|Co najmniej podpisany 8-bitową wartość|
|**_I8_MAX**|127i8|Maksymalna podpisany 8-bitową wartość|
|**_UI8_MAX**|0xffui8|Maksymalna wartość 8-bitowych unsigned|
|**_I16_MIN**|(- 32767i16 - 1)|Co najmniej podpisany 16-bitową wartość|
|**_I16_MAX**|32767i16|Maksymalna podpisany 16-bitową wartość|
|**_UI16_MAX**|0xffffui16|Maksymalna wartość 16-bitowych unsigned|
|**_I32_MIN**|(- 2147483647i32 - 1)|Co najmniej podpisany 32-bitową wartość|
|**_I32_MAX**|2147483647i32|Maksymalna podpisany 32-bitową wartość|
|**_UI32_MAX**|0xffffffffui32|Maksymalna wartość 32-bitowa bez znaku|
|**_I64_MIN**|(-9223372036854775807 - 1)|Co najmniej podpisany 64-bitową wartość|
|**_I64_MAX**|9223372036854775807|Maksymalna podpisany 64-bitową wartość|
|**_UI64_MAX**|0xffffffffffffffffui64|Wartość maksymalna 64-bitowych unsigned|
|**_I128_MIN**|(- 170141183460469231731687303715884105727i128 - 1)|Co najmniej podpisany 128-bitowej wartości|
|**_I128_MAX**|170141183460469231731687303715884105727i128|Maksymalna podpisany 128-bitowej wartości|
|**_UI128_MAX**|0xffffffffffffffffffffffffffffffffui128|Maksymalna wartość 128-bitowego bez znaku|
|**SIZE_MAX**|taki sam jak **_UI64_MAX** Jeśli **_win64 —** jest zdefiniowany lub **uint_max —**|Maksymalna liczba całkowita macierzysty rozmiar|
|**RSIZE_MAX**|taki sam jak (**SIZE_MAX** >> 1)|Rozmiar całkowitą maksymalną bezpieczne biblioteki|

## <a name="floating-point-type-constants"></a>Stałe typów zmiennoprzecinkowych

Zapewniają następujące ograniczenia zakresu i inne właściwości **długi** **podwójne**, **podwójne** i **float** typów danych. Aby korzystać z tych stałe, Dołącz nagłówek float.h — w pliku źródłowego:

```C
#include <float.h>
```

|Stała|Wartość|Opis|
|--------------|-----------|-----------------|
|**DBL_DECIMAL_DIG**|17|Liczba cyfr dziesiętnych zaokrąglania dokładności|
|**DBL_DIG —**|15|Liczba cyfr dziesiętnych dokładności|
|**DBL_EPSILON —**|2.2204460492503131e-016|Najmniejsza tak, aby 1.0 + **dbl_epsilon —** ! = 1.0|
|**DBL_HAS_SUBNORM**|1|Obsługuje typ subnormal (Brak reprezentacji zmiennoprzecinkowej) liczb|
|**DBL_MANT_DIG —**|53|Liczba bitów mantysy (mantysa)|
|**DBL_MAX —**|1, 7976931348623158e + 308|Wartość maksymalna|
|**DBL_MAX_10_EXP —**|308|Maksymalna wykładnik dziesiętną|
|**DBL_MAX_EXP —**|1024|Maksymalna wykładnik binarne|
|**DBL_MIN —**|2.2250738585072014e-308|Co najmniej znormalizowany wartość dodatnią|
|**DBL_MIN_10_EXP —**|(-307)|Minimalna wykładnik dziesiętną|
|**DBL_MIN_EXP —**|(-1021)|Minimalna wykładnik binarne|
|**_DBL_RADIX —**|2|Podstawa wykładnika|
|**DBL_TRUE_MIN**|4.9406564584124654e-324|Minimalna wartość subnormal dodatnią|
|**FLT_DECIMAL_DIG**|9|Liczba cyfr dziesiętnych zaokrąglania dokładności|
|**FLT_DIG —**|6|Liczba cyfr dziesiętnych dokładności|
|**FLT_EPSILON —**|1.192092896e-07F|Najmniejsza tak, aby 1.0 + **flt_epsilon —** ! = 1.0|
|**FLT_HAS_SUBNORM**|1|Obsługuje typ subnormal (Brak reprezentacji zmiennoprzecinkowej) liczb|
|**FLT_MANT_DIG —**|24|Liczba bitów mantysy (mantysa)|
|**FLT_MAX —**|3.402823466e + 38F|Wartość maksymalna|
|**FLT_MAX_10_EXP —**|38|Maksymalna wykładnik dziesiętną|
|**FLT_MAX_EXP —**|128|Maksymalna wykładnik binarne|
|**FLT_MIN —**|1.175494351e-38F|Co najmniej znormalizowany wartość dodatnią|
|**FLT_MIN_10_EXP —**|(-37)|Minimalna wykładnik dziesiętną|
|**FLT_MIN_EXP —**|(-125)|Minimalna wykładnik binarne|
|**FLT_RADIX —**|2|Podstawa wykładnika|
|**FLT_TRUE_MIN**|1.401298464e-45F|Minimalna wartość subnormal dodatnią|
|**LDBL_DIG**|15|Liczba cyfr dziesiętnych dokładności|
|**LDBL_EPSILON**|2.2204460492503131e-016|Najmniejsza tak, aby 1.0 + **LDBL_EPSILON** ! = 1.0|
|**LDBL_HAS_SUBNORM**|1|Obsługuje typ subnormal (Brak reprezentacji zmiennoprzecinkowej) liczb|
|**LDBL_MANT_DIG**|53|Liczba bitów mantysy (mantysa)|
|**LDBL_MAX**|1, 7976931348623158e + 308|Wartość maksymalna|
|**LDBL_MAX_10_EXP**|308|Maksymalna wykładnik dziesiętną|
|**LDBL_MAX_EXP**|1024|Maksymalna wykładnik binarne|
|**LDBL_MIN**|2.2250738585072014e-308|Co najmniej znormalizowany wartość dodatnią|
|**LDBL_MIN_10_EXP**|(-307)|Minimalna wykładnik dziesiętną|
|**LDBL_MIN_EXP**|(-1021)|Minimalna wykładnik binarne|
|**_LDBL_RADIX**|2|Podstawa wykładnika|
|**LDBL_TRUE_MIN**|4.9406564584124654e-324|Minimalna wartość subnormal dodatnią|
|**DECIMAL_DIG**|taki sam jak **DBL_DECIMAL_DIG**|Domyślne (dwa razy) cyfr dziesiętnych zaokrąglania dokładności|

## <a name="see-also"></a>Zobacz także

[Stałe globalne](../c-runtime-library/global-constants.md)  

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
ms.openlocfilehash: d9d053611fb733d55424d01be2bab030fc49e6e0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215169"
---
# <a name="data-type-constants"></a>Typ danych — Stałe

Stałe typu danych to zależne od implementacji zakresy wartości dozwolone dla typów danych całkowitych i zmiennoprzecinkowych.

## <a name="integral-type-constants"></a>Stałe typu całkowitego

Te stałe dają zakresy dla całkowitych typów danych. Aby użyć tych stałych, Uwzględnij nagłówek Limits. h w pliku źródłowym:

```C
#include <limits.h>
```

> [!NOTE]
> [`/J`](../build/reference/j-default-char-type-is-unsigned.md)Opcja kompilatora zmienia domyślny **`char`** Typ z **`signed char`** na **`unsigned char`** .

|Stały|Wartość|Opis|
|--------------|-----------|-------------|
|**CHAR_BIT**|8|Liczba bitów w**`char`**|
|**SCHAR_MIN**|(-128)|**`signed char`** Wartość minimalna|
|**SCHAR_MAX**|127|**`signed char`** Wartość maksymalna|
|**UCHAR_MAX**|255 (0xFF)|**`unsigned char`** Wartość maksymalna|
|**CHAR_MIN**|(-128) (0 Jeśli **`/J`** użyto opcji)|**`char`** Wartość minimalna|
|**CHAR_MAX**|127 (255 Jeśli **`/J`** użyto opcji)|**`char`** Wartość maksymalna|
|**MB_LEN_MAX**|5|Maksymalna liczba bajtów w wielobajtowym**`char`**|
|**SHRT_MIN**|-32768|**`signed short`** Wartość minimalna|
|**SHRT_MAX**|32767|**`signed short`** Wartość maksymalna|
|**USHRT_MAX**|65535 (0xFFFF)|**`unsigned short`** Wartość maksymalna|
|**INT_MIN**|(-2147483647-1)|**`signed int`** Wartość minimalna|
|**INT_MAX**|2147483647|**`signed int`** Wartość maksymalna|
|**UINT_MAX**|4294967295 (0xffffffff)|**`unsigned int`** Wartość maksymalna|
|**LONG_MIN**|(-2147483647-1)|**`signed long`** Wartość minimalna|
|**LONG_MAX**|2147483647|**`signed long`** Wartość maksymalna|
|**ULONG_MAX**|4294967295UL (0xfffffffful)|**`unsigned long`** Wartość maksymalna|
|**LLONG_MIN**|(-9223372036854775807LL-1)|Minimum **`signed long long`** lub **`__int64`** wartość|
|**LLONG_MAX**|9223372036854775807LL|Maksimum **`signed long long`** lub **`__int64`** wartość|
|**ULLONG_MAX**|0xffffffffffffffffull|**`unsigned long long`** Wartość maksymalna|
|**_I8_MIN**|(-127i8-1)|Minimalna podpisana wartość 8-bitowa|
|**_I8_MAX**|127i8|Maksymalna podpisana wartość 8-bitowa|
|**_UI8_MAX**|0xffui8|Maksymalna wartość 8-bitowa bez znaku|
|**_I16_MIN**|(-32767i16-1)|Minimalna podpisana wartość 16-bitowa|
|**_I16_MAX**|32767i16|Maksymalna podpisana wartość 16-bitowa|
|**_UI16_MAX**|0xffffui16|Maksymalna wartość 16-bitowa bez znaku|
|**_I32_MIN**|(-2147483647i32-1)|Minimalna podpisana wartość 32-bitowa|
|**_I32_MAX**|2147483647i32|Maksymalna podpisana wartość 32-bitowa|
|**_UI32_MAX**|0xffffffffui32|Maksymalna niepodpisana wartość 32-bitowa|
|**_I64_MIN**|(-9223372036854775807-1)|Minimalna podpisana wartość 64-bitowa|
|**_I64_MAX**|9223372036854775807|Maksymalna podpisana wartość 64-bitowa|
|**_UI64_MAX**|0xffffffffffffffffui64|Maksymalna niepodpisana wartość 64-bitowa|
|**_I128_MIN**|(-170141183460469231731687303715884105727i128-1)|Minimalna podpisana wartość 128-bitowa|
|**_I128_MAX**|170141183460469231731687303715884105727i128|Maksymalna podpisana wartość 128-bitowa|
|**_UI128_MAX**|0xffffffffffffffffffffffffffffffffui128|Maksymalna niepodpisana wartość 128-bitowa|
|**SIZE_MAX**|tak samo jak **_UI64_MAX** , jeśli **_WIN64** jest zdefiniowany lub **UINT_MAX**|Maksymalny rozmiar natywnej wartości całkowitej|
|**RSIZE_MAX**|Analogicznie jak (**SIZE_MAX** >> 1)|Maksymalny rozmiar całkowitej biblioteki bezpiecznych|

## <a name="floating-point-type-constants"></a>Stałe typu zmiennoprzecinkowego

Poniższe stałe dają zakres i inne cechy **`long double`** **`double`** typów i **`float`** . Aby użyć tych stałych, Uwzględnij nagłówek float. h w pliku źródłowym:

```C
#include <float.h>
```

|Stały|Wartość|Opis|
|--------------|-----------|-----------------|
|**DBL_DECIMAL_DIG**|17|Liczba cyfr dziesiętnych dokładności zaokrąglania|
|**DBL_DIG**|15|Liczba cyfr dziesiętnych dokładności|
|**DBL_EPSILON**|2.2204460492503131 e-016|Najmniejszy taki, że 1,0 + **DBL_EPSILON** ! = 1,0|
|**DBL_HAS_SUBNORM**|1|Typ obsługuje liczby podnormalne (nienormalne)|
|**DBL_MANT_DIG**|53|Liczba bitów w mantysę (mantysy)|
|**DBL_MAX**|1.7976931348623158 e + 308|Wartość maksymalna|
|**DBL_MAX_10_EXP**|308|Maksymalny wykładnik dziesiętny|
|**DBL_MAX_EXP**|1024|Maksymalny wykładnik binarny|
|**DBL_MIN**|2.2250738585072014 e-308|Minimalna znormalizowana wartość dodatnia|
|**DBL_MIN_10_EXP**|(-307)|Minimalny wykładnik dziesiętny|
|**DBL_MIN_EXP**|(-1021)|Minimalny wykładnik binarny|
|**_DBL_RADIX**|2|Podstawy wykładnika|
|**DBL_TRUE_MIN**|4.9406564584124654 e-324|Minimalna dodatnia wartość nienormalna|
|**FLT_DECIMAL_DIG**|9|Liczba cyfr dziesiętnych dokładności zaokrąglania|
|**FLT_DIG**|6|Liczba cyfr dziesiętnych dokładności|
|**FLT_EPSILON**|1.192092896 e-07F|Najmniejszy taki, że 1,0 + **FLT_EPSILON** ! = 1,0|
|**FLT_HAS_SUBNORM**|1|Typ obsługuje liczby podnormalne (nienormalne)|
|**FLT_MANT_DIG**|24|Liczba bitów w mantysę (mantysy)|
|**FLT_MAX**|3.402823466 e + 38F|Wartość maksymalna|
|**FLT_MAX_10_EXP**|38|Maksymalny wykładnik dziesiętny|
|**FLT_MAX_EXP**|128|Maksymalny wykładnik binarny|
|**FLT_MIN**|1.175494351 e-38F|Minimalna znormalizowana wartość dodatnia|
|**FLT_MIN_10_EXP**|(-37)|Minimalny wykładnik dziesiętny|
|**FLT_MIN_EXP**|(-125)|Minimalny wykładnik binarny|
|**FLT_RADIX**|2|Podstawy wykładnika|
|**FLT_TRUE_MIN**|1.401298464 e-45F|Minimalna dodatnia wartość nienormalna|
|**LDBL_DIG**|15|Liczba cyfr dziesiętnych dokładności|
|**LDBL_EPSILON**|2.2204460492503131 e-016|Najmniejszy taki, że 1,0 + **LDBL_EPSILON** ! = 1,0|
|**LDBL_HAS_SUBNORM**|1|Typ obsługuje liczby podnormalne (nienormalne)|
|**LDBL_MANT_DIG**|53|Liczba bitów w mantysę (mantysy)|
|**LDBL_MAX**|1.7976931348623158 e + 308|Wartość maksymalna|
|**LDBL_MAX_10_EXP**|308|Maksymalny wykładnik dziesiętny|
|**LDBL_MAX_EXP**|1024|Maksymalny wykładnik binarny|
|**LDBL_MIN**|2.2250738585072014 e-308|Minimalna znormalizowana wartość dodatnia|
|**LDBL_MIN_10_EXP**|(-307)|Minimalny wykładnik dziesiętny|
|**LDBL_MIN_EXP**|(-1021)|Minimalny wykładnik binarny|
|**_LDBL_RADIX**|2|Podstawy wykładnika|
|**LDBL_TRUE_MIN**|4.9406564584124654 e-324|Minimalna dodatnia wartość nienormalna|
|**DECIMAL_DIG**|taki sam jak **DBL_DECIMAL_DIG**|Domyślne (podwójne) cyfry dziesiętne dokładności zaokrąglania|

## <a name="see-also"></a>Zobacz także

[Stałe globalne](../c-runtime-library/global-constants.md)

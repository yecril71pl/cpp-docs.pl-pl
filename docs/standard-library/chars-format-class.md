---
title: chars_format Wyliczenie
ms.date: 07/22/2020
f1_keywords:
- charconv/std::chars_format
helpviewer_keywords:
- std::chars_format
ms.openlocfilehash: 4c1d495c943be02b66d52d1986a783b29a8009c5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230185"
---
# <a name="chars_format-enum"></a>chars_format Wyliczenie

Używany z [\<charconv>](charconv.md) biblioteką do określenia formatu zmiennoprzecinkowego konwersji liczb pierwotnych.

## <a name="syntax"></a>Składnia

```cpp
enum class chars_format {
    scientific = unspecified,
    fixed = unspecified,
    hex = unspecified,
    general = fixed | scientific
};
```

### <a name="members"></a>Elementy członkowskie

|Element|Opis|
|-|-|
| `scientific` | Powoduje `from_chars()` oczekiwanie i przeanalizowanie wykładnika. Przypomina `'e'` `printf()` specyfikator formatu, który formatuje notację naukową, taką jak`"1.729e+01"` |
| `fixed` | Powoduje `from_chars()` , że nie oczekuje się lub nie przeanalizuje wykładnika. Przypomina `'f'` `printf()` specyfikator formatu, który formatuje zmiennoprzecinkowe, na przykład `"17.29"` .|
| `hex` | Powoduje `from_chars()` , że liczba jest oczekiwana w formacie szesnastkowym, ale bez wiodącego znaku "0x". |
| `general` | Powoduje `from_chars()` zaakceptowanie (ale nie wymaganie) wykładnika. Dla `to_chars()` , jest podobny do `g` specyfikatora formatu printf (), który przełącza między notacją naukową lub naprawioną. Należy wziąć pod uwagę znaczenie wykładnika, która będzie mogła generować odpowiednio zwarte dane wyjściowe. Na przykład: `1e-5` wyniki w `"1e-05"` , ale są `1e-4` wynikiem `"0.001"` . `1e5`wyniki w `100000` `1e6` `1e+06` . `1e0`tworzy `1` .|

## <a name="remarks"></a>Uwagi

W przypadku funkcji [from_chars](charconv-functions.md#from_chars) w tym wyliczeniu opisano rodzaj danych wejściowych, których oczekujesz.
W przypadku funkcji [to_chars](charconv-functions.md#to_chars) opisuje rodzaj danych wyjściowych do emisji.

## <a name="see-also"></a>Zobacz także

[\<charconv>](../standard-library/charconv.md)  
[specyfikatory formatu printf ()](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)

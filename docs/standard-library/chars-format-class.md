---
title: chars_format Wyliczenie
ms.date: 08/03/2020
f1_keywords:
- charconv/std::chars_format
helpviewer_keywords:
- std::chars_format
ms.openlocfilehash: d7f95d9bd1522fa0896ccdbac6c1dbc770f2b272
ms.sourcegitcommit: 4eda68a0b3c23d8cefa56b7ba11583412459b32f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/04/2020
ms.locfileid: "87565940"
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
| `scientific` | Powoduje `from_chars()` oczekiwanie i przeanalizowanie wykładnika. Przypomina `printf()` specyfikator formatu `'e'` , który formatuje notację wykładniczą, np `"1.729e+01"` . |
| `fixed` | Powoduje `from_chars()` , że nie oczekuje się lub nie przeanalizuje wykładnika. Przypomina `printf()` specyfikator formatu `'f'` , który formatuje zmiennoprzecinkowe, na przykład `"17.29"` .|
| `hex` | Powoduje `from_chars()` , że liczba jest oczekiwana w formacie szesnastkowym, ale bez wiodącego `0x` . |
| `general` | Powoduje `from_chars()` zaakceptowanie (ale nie wymaganie) wykładnika. Dla `to_chars()` , jest podobny do `printf()` specyfikatora formatu `'g'` , który przełącza między notacją naukową lub naprawioną. Należy wziąć pod uwagę znaczenie wykładnika, która będzie mogła generować odpowiednio zwarte dane wyjściowe. Na przykład: `1e-5` wyniki w `"1e-05"` , ale są `1e-4` wynikiem `"0.001"` . `1e5`wyniki w `100000` `1e6` `1e+06` . `1e0`tworzy `1` .|

## <a name="remarks"></a>Uwagi

W przypadku funkcji [from_chars](charconv-functions.md#from_chars) w tym wyliczeniu opisano rodzaj danych wejściowych, których oczekujesz.
W przypadku funkcji [to_chars](charconv-functions.md#to_chars) opisuje rodzaj danych wyjściowych do emisji.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<charconv>

**Przestrzeń nazw:** std

wymagany jest/std: c++ 17 lub nowszy.

## <a name="see-also"></a>Zobacz też

[\<charconv>](../standard-library/charconv.md)  
[specyfikatory formatu printf ()](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)

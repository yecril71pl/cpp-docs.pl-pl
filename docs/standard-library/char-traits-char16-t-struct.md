---
title: char_traits&lt;—&gt; struktura char16_t
ms.date: 11/04/2016
f1_keywords:
- char_traits<char16_t>
- iosfwd/std::char_traits<char16_t>
helpviewer_keywords:
- char_traits<char16_t> class
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
ms.openlocfilehash: d83f5278c2c4f8344334bfce40946612e9ca3e56
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448961"
---
# <a name="chartraitsltchar16tgt-struct"></a>char_traits&lt;—&gt; struktura char16_t

Struktura, która jest specjalizacją struktury szablonu **\<char_traits CharType >** do elementu typu. `char16_t`

## <a name="syntax"></a>Składnia

```cpp
template <>
struct char_traits<char16_t>;
```

## <a name="remarks"></a>Uwagi

Specjalizacja umożliwia strukturze korzystanie z funkcji bibliotek, które manipulują obiektami typu `char16_t`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ciąg >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<string>](../standard-library/string.md)\
[char_traits, struktura](../standard-library/char-traits-struct.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

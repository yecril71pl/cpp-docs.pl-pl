---
title: '&lt;struktura char16_t &gt; char_traits'
ms.date: 11/04/2016
f1_keywords:
- char_traits<char16_t>
- iosfwd/std::char_traits<char16_t>
helpviewer_keywords:
- char_traits<char16_t> class
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
ms.openlocfilehash: 53a77ff993d3a99cae1ec8e48a06dd7800ce74c7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230223"
---
# <a name="char_traitsltchar16_tgt-struct"></a>&lt;struktura char16_t &gt; char_traits

Struktura, która jest specjalizacją struktury szablonu **char_traits \<CharType> ** do elementu typu **`char16_t`** .

## <a name="syntax"></a>Składnia

```cpp
template <>
struct char_traits<char16_t>;
```

## <a name="remarks"></a>Uwagi

Specjalizacja umożliwia strukturze korzystanie z funkcji bibliotek, które manipulują obiektami typu **`char16_t`** .

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<string>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<string>](../standard-library/string.md)\
[Struktura char_traits](../standard-library/char-traits-struct.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

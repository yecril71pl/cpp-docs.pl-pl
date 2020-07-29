---
title: '&lt;struktura wchar_t &gt; char_traits'
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: 3b2504dbb124ccca7f9b27619585abb2b5795f92
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219173"
---
# <a name="char_traitsltwchar_tgt-struct"></a>&lt;struktura wchar_t &gt; char_traits

Klasa, która jest specjalizacją struktury szablonu **char_traits \<CharType> ** do elementu typu **`wchar_t`** .

## <a name="syntax"></a>Składnia

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>Uwagi

Specjalizacja umożliwia strukturze korzystanie z funkcji bibliotek, które manipulują obiektami tego typu **`wchar_t`** .

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<string>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Struktura char_traits](../standard-library/char-traits-struct.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

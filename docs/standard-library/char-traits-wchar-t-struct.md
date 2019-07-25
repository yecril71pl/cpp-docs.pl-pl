---
title: char_traits&lt;—&gt; struktura wchar_t
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: a2f8a882020ddb3d87436d08b3d85ea9407b1c08
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458975"
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;—&gt; struktura wchar_t

Klasa, która jest specjalizacją struktury szablonu **char_traits\<CharType >** do elementu typu **wchar_t**.

## <a name="syntax"></a>Składnia

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>Uwagi

Specjalizacja umożliwia strukturze korzystanie z funkcji bibliotek, które manipulują obiektami tego typu **wchar_t**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ciąg >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[char_traits, struktura](../standard-library/char-traits-struct.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

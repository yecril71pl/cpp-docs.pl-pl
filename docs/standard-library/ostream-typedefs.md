---
title: '&lt;ostream&gt; Typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 18f30a12a6f4d2b97cb5dca3ace98e6241d856a7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447153"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; Typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>ostream

Tworzy typ z basic_ostream, który jest wyspecjalizowany  dla char `char_traits` i wyspecjalizowany dla **char**.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla klasy szablonu [basic_ostream](../standard-library/basic-ostream-class.md), wyspecjalizowany dla elementów typu **char** z domyślnymi cechami znaków.

## <a name="wostream"></a>wostream —

Tworzy typ z basic_ostream, który jest wyspecjalizowany  w wchar_t `char_traits` i wyspecjalizowany dla **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla klasy szablonu [basic_ostream](../standard-library/basic-ostream-class.md), wyspecjalizowany dla elementów typu **wchar_t** z cechami domyślnymi znaków.

## <a name="see-also"></a>Zobacz także

[\<ostream>](../standard-library/ostream.md)

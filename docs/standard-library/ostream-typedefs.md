---
title: '&lt;ostream &gt; Typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: a61eeb98dfd275b10749e86043a3f7042be84ab9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224659"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream &gt; Typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream —](#wostream)|

## <a name="ostream"></a><a name="ostream"></a>ostream

Tworzy typ z basic_ostream, który jest wyspecjalizowany **`char`** i `char_traits` wyspecjalizowany dla **`char`** .

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ostream](../standard-library/basic-ostream-class.md), wyspecjalizowany dla elementów typu **`char`** z cechami domyślnymi znaków.

## <a name="wostream"></a><a name="wostream"></a>wostream —

Tworzy typ z basic_ostream, który jest wyspecjalizowany **`wchar_t`** i `char_traits` wyspecjalizowany dla **`wchar_t`** .

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ostream](../standard-library/basic-ostream-class.md), wyspecjalizowany dla elementów typu **`wchar_t`** z cechami domyślnymi znaków.

## <a name="see-also"></a>Zobacz także

[\<ostream>](../standard-library/ostream.md)

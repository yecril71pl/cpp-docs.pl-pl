---
title: '&lt;ostream&gt; Typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: d0ceae12069712c7a124990d0f81968c21bc683a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419715"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; Typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream —](#wostream)|

## <a name="ostream"></a>ostream

Tworzy typ z basic_ostream, który jest wyspecjalizowany dla **znaków** i `char_traits` wyspecjalizowany dla **char**.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ostream](../standard-library/basic-ostream-class.md), wyspecjalizowany dla elementów typu **char** z domyślnymi cechami znaków.

## <a name="wostream"></a>wostream —

Tworzy typ z basic_ostream, który jest wyspecjalizowany dla **wchar_t** i `char_traits` wyspecjalizowany na **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ostream](../standard-library/basic-ostream-class.md), wyspecjalizowany dla elementów typu **wchar_t** z cechami domyślnymi znaków.

## <a name="see-also"></a>Zobacz też

[\<ostream >](../standard-library/ostream.md)

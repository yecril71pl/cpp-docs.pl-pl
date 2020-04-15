---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 82539a3fdadf10d340ca957756e235e8ae00b267
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373581"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[Ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a><a name="ostream"></a>Ostream

Tworzy typ z basic_ostream, który specjalizuje `char_traits` się w **char** i specjalizuje się w **char**.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_ostream,](../standard-library/basic-ostream-class.md)wyspecjalizowane dla elementów **typu char** z domyślnymi cechami znaków.

## <a name="wostream"></a><a name="wostream"></a>wostream

Tworzy typ z basic_ostream, który specjalizuje się w `char_traits` **wchar_t** i specjalizuje się w **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_ostream,](../standard-library/basic-ostream-class.md)wyspecjalizowanym dla elementów typu **wchar_t** z domyślnymi cechami znaków.

## <a name="see-also"></a>Zobacz też

[\<>ostream](../standard-library/ostream.md)

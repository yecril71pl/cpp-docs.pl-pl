---
title: '&lt;streambuf &gt; Typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: f08c08de0d6449714f953f5a65fadd2e0279ed44
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843199"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf &gt; Typedefs

[streambuf](#streambuf)\
[wstreambuf —](#wstreambuf)

## <a name="streambuf"></a><a name="streambuf"></a> streambuf

Specjalizacja `basic_streambuf` , która używa **`char`** jako parametrów szablonu.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_streambuf](../standard-library/basic-streambuf-class.md), wyspecjalizowany dla elementów typu **`char`** z cechami domyślnymi znaków.

## <a name="wstreambuf"></a><a name="wstreambuf"></a> wstreambuf —

Specjalizacja `basic_streambuf` , która używa **`wchar_t`** jako parametrów szablonu.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_streambuf](../standard-library/basic-streambuf-class.md), wyspecjalizowany dla elementów typu **`wchar_t`** z cechami domyślnymi znaków.

## <a name="see-also"></a>Zobacz też

[\<streambuf>](../standard-library/streambuf.md)

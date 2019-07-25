---
title: '&lt;streambuf&gt; Typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 178b489d92a4ed7340084490329fdf8fa16c2aa7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449587"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; Typedefs

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>streambuf

Specjalizacja `basic_streambuf` , która używa **znaków** jako parametrów szablonu.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla klasy szablonu [basic_streambuf](../standard-library/basic-streambuf-class.md), wyspecjalizowany dla elementów typu **char** z domyślnymi cechami znaków.

## <a name="wstreambuf"></a>wstreambuf —

Specjalizacja `basic_streambuf` , która używa **wchar_t** jako parametrów szablonu.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla klasy szablonu [basic_streambuf](../standard-library/basic-streambuf-class.md), wyspecjalizowany dla elementów typu **wchar_t** z cechami domyślnymi znaków.

## <a name="see-also"></a>Zobacz także

[\<streambuf>](../standard-library/streambuf.md)

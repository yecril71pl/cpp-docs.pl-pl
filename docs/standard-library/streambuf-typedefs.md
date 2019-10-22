---
title: '&lt;streambuf &gt; Typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 1c9850ad7d7ec9b9c3554e6806f4790ef3613b08
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688939"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf &gt; Typedefs

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf —](#wstreambuf)|

## <a name="streambuf"></a>streambuf

Specjalizacja `basic_streambuf`, która używa **znaków** jako parametrów szablonu.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_streambuf](../standard-library/basic-streambuf-class.md), wyspecjalizowany dla elementów typu **char** z domyślnymi cechami znaków.

## <a name="wstreambuf"></a>wstreambuf —

Specjalizacja `basic_streambuf`, która używa **wchar_t** jako parametrów szablonu.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_streambuf](../standard-library/basic-streambuf-class.md), wyspecjalizowany dla elementów typu **wchar_t** z cechami domyślnymi znaków.

## <a name="see-also"></a>Zobacz także

[\<streambuf >](../standard-library/streambuf.md)

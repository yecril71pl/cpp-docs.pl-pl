---
title: '&lt;streambuf&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 8eb058f161a9f30ccf5e9d49307b50c215f79c22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376681"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedefs

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a><a name="streambuf"></a>streambuf

`basic_streambuf` Specjalizacja, która używa **char** jako parametrów szablonu.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_streambuf,](../standard-library/basic-streambuf-class.md)wyspecjalizowane dla elementów **typu char** z domyślnymi cechami znaków.

## <a name="wstreambuf"></a><a name="wstreambuf"></a>wstreambuf

`basic_streambuf` Specjalizacja, która używa **wchar_t** jako parametrów szablonu.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_streambuf,](../standard-library/basic-streambuf-class.md)wyspecjalizowane dla elementów typu **wchar_t** z domyślnymi cechami znaków.

## <a name="see-also"></a>Zobacz też

[\<>streambuf](../standard-library/streambuf.md)

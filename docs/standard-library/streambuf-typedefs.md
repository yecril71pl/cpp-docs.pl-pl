---
title: '&lt;streambuf —&gt; definicje typów'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 505739861771a05dd39741f432579a6e9b2d0c26
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664064"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf —&gt; definicje typów

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf —

Specjalizacja `basic_streambuf` , który używa **char** jako parametry szablonu.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla klasy szablonu [basic_streambuf](../standard-library/basic-streambuf-class.md), wyspecjalizowany dla elementów typu **char** przy użyciu domyślnego cech.

## <a name="wstreambuf"></a>  wstreambuf

Specjalizacja `basic_streambuf` , który używa **wchar_t** jako parametry szablonu.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla klasy szablonu [basic_streambuf](../standard-library/basic-streambuf-class.md), wyspecjalizowany dla elementów typu **wchar_t** przy użyciu domyślnego cech.

## <a name="see-also"></a>Zobacz także

[\<streambuf>](../standard-library/streambuf.md)<br/>

---
title: '&lt;streambuf —&gt; definicje typów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 81c7cd875c6083ee77701116f6b1179760373ec0
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953995"
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

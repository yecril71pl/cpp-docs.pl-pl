---
title: '&lt;streambuf&gt; definicje typów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 8fb1713dfbc2d9766c488f21d324d801a4886d68
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854220"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; definicje typów

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

Specjalizacji `basic_streambuf` używającą `char` jako parametry szablonu.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem klasy szablonu [basic_streambuf —](../standard-library/basic-streambuf-class.md), wyspecjalizowany dla elementów typu `char` z domyślnego cech znaków.

## <a name="wstreambuf"></a>  wstreambuf

Specjalizacji `basic_streambuf` używającą `wchar_t` jako parametry szablonu.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem klasy szablonu [basic_streambuf —](../standard-library/basic-streambuf-class.md), wyspecjalizowany dla elementów typu `wchar_t` z domyślnego cech znaków.

## <a name="see-also"></a>Zobacz także

[\<streambuf>](../standard-library/streambuf.md)<br/>

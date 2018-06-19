---
title: '&lt;ostream&gt; definicje typów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 3f5511cfbf73ddf74fa12954e1a108d8accf875e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852582"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; definicje typów

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

Tworzy typ na podstawie basic_ostream —, które jest przeznaczone na `char` i `char_traits` specjalne na `char`.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ostream —](../standard-library/basic-ostream-class.md), wyspecjalizowany dla elementów typu `char` z domyślnego cech znaków.

## <a name="wostream"></a>  wostream

Tworzy typ na podstawie basic_ostream —, które jest przeznaczone na `wchar_t` i `char_traits` specjalne na `wchar_t`.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ostream —](../standard-library/basic-ostream-class.md), wyspecjalizowany dla elementów typu `wchar_t` z domyślnego cech znaków.

## <a name="see-also"></a>Zobacz także

[\<ostream>](../standard-library/ostream.md)<br/>

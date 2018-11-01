---
title: '&lt;ostream&gt; definicje typów'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 02936fdfc990ea65a99b2875cf7f482eb2ce4ebe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429747"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; definicje typów

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

Tworzy typ na podstawie basic_ostream, które jest przeznaczone na **char** i `char_traits` wyspecjalizowane na **char**.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ostream](../standard-library/basic-ostream-class.md), wyspecjalizowany dla elementów typu **char** przy użyciu domyślnego cech.

## <a name="wostream"></a>  wostream

Tworzy typ na podstawie basic_ostream, które jest przeznaczone na **wchar_t** i `char_traits` wyspecjalizowane na **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ostream](../standard-library/basic-ostream-class.md), wyspecjalizowany dla elementów typu **wchar_t** przy użyciu domyślnego cech.

## <a name="see-also"></a>Zobacz także

[\<ostream>](../standard-library/ostream.md)<br/>

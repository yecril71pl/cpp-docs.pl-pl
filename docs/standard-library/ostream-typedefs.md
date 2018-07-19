---
title: '&lt;ostream&gt; definicje typów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 094952a76d8e46e4244cf57a8c5a47c929f3ae37
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960357"
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

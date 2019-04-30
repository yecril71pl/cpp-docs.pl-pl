---
title: '&lt;IStream&gt; definicje typów'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: f647fba2036f6c69cb02393e30553c66df34b9dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413297"
---
# <a name="ltistreamgt-typedefs"></a>&lt;IStream&gt; definicje typów

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>  iostream

Typ `basic_iostream` wyspecjalizowane na **char**.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_iostream —](../standard-library/basic-iostream-class.md), wyspecjalizowany dla elementów typu **char** przy użyciu domyślnego cech.

## <a name="istream"></a>  IStream

Typ `basic_istream` wyspecjalizowane na **char**.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_istream](../standard-library/basic-istream-class.md), wyspecjalizowany dla elementów typu **char** przy użyciu domyślnego cech.

## <a name="wiostream"></a>  wiostream

Typ `basic_iostream` wyspecjalizowane na **wchar_t**.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_iostream —](../standard-library/basic-iostream-class.md), wyspecjalizowany dla elementów typu **wchar_t** przy użyciu domyślnego cech.

## <a name="wistream"></a>  wistream

Typ `basic_istream` wyspecjalizowane na **wchar_t**.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_istream](../standard-library/basic-istream-class.md), wyspecjalizowany dla elementów typu **wchar_t** przy użyciu domyślnego cech.

## <a name="see-also"></a>Zobacz także

[\<istream>](../standard-library/istream.md)<br/>

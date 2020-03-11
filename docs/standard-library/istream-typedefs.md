---
title: '&lt;IStream&gt; Typedefs'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: 9a25e4aa9ee42ea36d1bb8d6b196b36ff5c97758
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856598"
---
# <a name="ltistreamgt-typedefs"></a>&lt;IStream&gt; Typedefs

||||
|-|-|-|
|[iostream](#iostream)|[IStream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>iostream

Typ `basic_iostream` wyspecjalizowany dla **znaku**.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_iostream](../standard-library/basic-iostream-class.md), wyspecjalizowany dla elementów typu **char** z domyślnymi cechami znaków.

## <a name="istream"></a>IStream

Typ `basic_istream` wyspecjalizowany dla **znaku**.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_istream](../standard-library/basic-istream-class.md), wyspecjalizowany dla elementów typu **char** z domyślnymi cechami znaków.

## <a name="wiostream"></a>wiostream

Typ `basic_iostream` wyspecjalizowany w **wchar_t**.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_iostream](../standard-library/basic-iostream-class.md), wyspecjalizowany dla elementów typu **wchar_t** z cechami domyślnymi znaków.

## <a name="wistream"></a>wistream

Typ `basic_istream` wyspecjalizowany w **wchar_t**.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_istream](../standard-library/basic-istream-class.md), wyspecjalizowany dla elementów typu **wchar_t** z cechami domyślnymi znaków.

## <a name="see-also"></a>Zobacz także

[\<IStream >](../standard-library/istream.md)

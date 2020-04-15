---
title: '&lt;istream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: e9228bddcc3b99503b6b5f0e93b5ed6eeed773d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363086"
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt; typedefs

||||
|-|-|-|
|[iostream](#iostream)|[Istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a><a name="iostream"></a>Iostream

Typ `basic_iostream` wyspecjalizowany na **char**.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_iostream,](../standard-library/basic-iostream-class.md)wyspecjalizowane dla elementów **typu char** z domyślnymi cechami znaków.

## <a name="istream"></a><a name="istream"></a>Istream

Typ `basic_istream` wyspecjalizowany na **char**.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_istream,](../standard-library/basic-istream-class.md)wyspecjalizowane dla elementów **typu char** z domyślnymi cechami znaków.

## <a name="wiostream"></a><a name="wiostream"></a>wiostream

Typ `basic_iostream` specjalizujący się **w wchar_t**.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_iostream,](../standard-library/basic-iostream-class.md)wyspecjalizowanym dla elementów typu **wchar_t** z domyślnymi cechami znaków.

## <a name="wistream"></a><a name="wistream"></a>wistream

Typ `basic_istream` specjalizujący się **w wchar_t**.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_istream,](../standard-library/basic-istream-class.md)wyspecjalizowanym dla elementów typu **wchar_t** z domyślnymi cechami znaków.

## <a name="see-also"></a>Zobacz też

[\<>istream](../standard-library/istream.md)

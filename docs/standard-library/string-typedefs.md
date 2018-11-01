---
title: '&lt;ciąg&gt; definicje typów'
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 534c51e8a627ca893ea42e023f12d8bc62d6fb5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456280"
---
# <a name="ltstringgt-typedefs"></a>&lt;ciąg&gt; definicje typów

||||
|-|-|-|
|[string](#string)|[u16string](#u16string)|[u32string](#u32string)|
|[wstring](#wstring)|

## <a name="string"></a>  ciąg

Typ, który opisuje specjalizacji szablonu klasy [basic_string](../standard-library/basic-string-class.md) elementami typu **char**.

Inne definicje typów, które specialize `basic_string` obejmują [wstring](../standard-library/string-typedefs.md#wstring), [u16string](../standard-library/string-typedefs.md#u16string), i [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>Uwagi

Równoważne deklaracji są następujące:

```cpp
string str("");

basic_string<char> str("");
```

Aby uzyskać listę parametrów konstruktorów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string"></a>  u16string

Typ, który opisuje specjalizacji szablonu klasy [basic_string](../standard-library/basic-string-class.md) elementami typu `char16_t`.

Inne definicje typów, które specialize `basic_string` obejmują [wstring](../standard-library/string-typedefs.md#wstring), [ciąg](../standard-library/string-typedefs.md#string), i [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać listę parametrów konstruktorów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string"></a>  u32string

Typ, który opisuje specjalizacji szablonu klasy [basic_string](../standard-library/basic-string-class.md) elementami typu `char32_t`.

Inne definicje typów, które specialize `basic_string` obejmują [ciąg](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string), i [wstring](../standard-library/string-typedefs.md#wstring).

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać listę parametrów konstruktorów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring"></a>  wstring

Typ, który opisuje specjalizacji szablonu klasy [basic_string](../standard-library/basic-string-class.md) elementami typu **wchar_t**.

Inne definicje typów, które specialize `basic_string` obejmują [ciąg](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string), i [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>Uwagi

Równoważne deklaracji są następujące:

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

Aby uzyskać listę parametrów konstruktorów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Rozmiar **wchar_t** jest zdefiniowane w implementacji. Jeśli Twój kod jest zależna od **wchar_t** do określonego rozmiaru, zapoznaj się z implementacji danej platformy (na przykład za pomocą `sizeof(wchar_t)`). Jeśli potrzebujesz typu ciąg znaków o szerokości, który gwarantuje pozostają takie same na wszystkich platformach, należy użyć [ciąg](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string), lub [u32string](../standard-library/string-typedefs.md#u32string).

## <a name="see-also"></a>Zobacz także

[\<ciąg >](../standard-library/string.md)<br/>

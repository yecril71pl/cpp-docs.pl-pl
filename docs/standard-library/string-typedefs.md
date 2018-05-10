---
title: '&lt;ciąg&gt; definicje typów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 2d3f63ab29049e5f5a928186ba033bfe041bcfc1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltstringgt-typedefs"></a>&lt;ciąg&gt; definicje typów

||||
|-|-|-|
|[string](#string)|[u16string](#u16string)|[u32string](#u32string)|
|[wstring](#wstring)|

## <a name="string"></a>  Ciąg

Typ, który opisuje specjalizacji szablonu klasy [basic_string —](../standard-library/basic-string-class.md) elementami typu `char`.

Inne definicje typów, które specialize `basic_string` obejmują [wstring](../standard-library/string-typedefs.md#wstring), [u16string](../standard-library/string-typedefs.md#u16string), i [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>Uwagi

Deklaracje równoważne są następujące:

```cpp
string str("");

basic_string<char> str("");
```

Lista konstruktorów ciągu, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string"></a>  u16string

Typ, który opisuje specjalizacji szablonu klasy [basic_string —](../standard-library/basic-string-class.md) elementami typu `char16_t`.

Inne definicje typów, które specialize `basic_string` obejmują [wstring](../standard-library/string-typedefs.md#wstring), [ciąg](../standard-library/string-typedefs.md#string), i [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>Uwagi

Lista konstruktorów ciągu, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string"></a>  u32string

Typ, który opisuje specjalizacji szablonu klasy [basic_string —](../standard-library/basic-string-class.md) elementami typu `char32_t`.

Inne definicje typów, które specialize `basic_string` obejmują [ciąg](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string), i [wstring](../standard-library/string-typedefs.md#wstring).

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>Uwagi

Lista konstruktorów ciągu, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring"></a>  wstring

Typ, który opisuje specjalizacji szablonu klasy [basic_string —](../standard-library/basic-string-class.md) elementami typu `wchar_t`.

Inne definicje typów, które specialize `basic_string` obejmują [ciąg](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string), i [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>Uwagi

Deklaracje równoważne są następujące:

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

Lista konstruktorów ciągu, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Rozmiar `wchar_t` jest zdefiniowane w implementacji. Jeśli kod jest zależny od `wchar_t` się określony rozmiar, sprawdź implementacji danej platformy (na przykład z `sizeof(wchar_t)`). Jeśli potrzebujesz typu ciąg znaków o szerokości, który jest taka sama na wszystkich platformach gwarantuje, że, użyj [ciąg](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string), lub [u32string](../standard-library/string-typedefs.md#u32string).

## <a name="see-also"></a>Zobacz także

[\<ciąg >](../standard-library/string.md)<br/>

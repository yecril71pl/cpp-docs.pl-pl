---
title: ciąg &lt;&gt; Typedefs
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 950ca5ae34b6469c3d79b7297d4fe7b7644d2fcf
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419498"
---
# <a name="ltstringgt-typedefs"></a>ciąg &lt;&gt; Typedefs

||||
|-|-|-|
|[string](#string)|[u16string](#u16string)|[u32string](#u32string)|
|[wstring](#wstring)|

## <a name="string"></a>parametry

Typ, który opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) z elementami typu **char**.

Inne definicje typów, które są wyspecjalizowane `basic_string` zawierają [wstring](../standard-library/string-typedefs.md#wstring), [u16string](../standard-library/string-typedefs.md#u16string)i [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>Uwagi

Poniżej przedstawiono równoważne deklaracje:

```cpp
string str("");

basic_string<char> str("");
```

Aby zapoznać się z listą konstruktorów ciągów, zobacz [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string"></a>u16string

Typ, który opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) z elementami typu `char16_t`.

Inne definicje typów, które są wyspecjalizowane `basic_string` zawierają [wstring](../standard-library/string-typedefs.md#wstring), [String](../standard-library/string-typedefs.md#string)i [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>Uwagi

Aby zapoznać się z listą konstruktorów ciągów, zobacz [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string"></a>u32string

Typ, który opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) z elementami typu `char32_t`.

Inne definicje typów, które są wyspecjalizowane `basic_string` zawierają [ciąg](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)i [wstring](../standard-library/string-typedefs.md#wstring).

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>Uwagi

Aby zapoznać się z listą konstruktorów ciągów, zobacz [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring"></a>wstring

Typ, który opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) z elementami typu **wchar_t**.

Inne definicje typów, które są wyspecjalizowane `basic_string` zawierają [ciąg](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)i [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>Uwagi

Poniżej przedstawiono równoważne deklaracje:

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

Aby zapoznać się z listą konstruktorów ciągów, zobacz [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Rozmiar **wchar_t** jest zdefiniowany przez implementację. Jeśli kod zależy od **wchar_t** ma określony rozmiar, sprawdź implementację platformy (na przykład z `sizeof(wchar_t)`). Jeśli potrzebujesz typu ciągu o szerokości, która gwarantuje, że pozostaje taka sama na wszystkich platformach, użyj [String](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)lub [u32string](../standard-library/string-typedefs.md#u32string).

## <a name="see-also"></a>Zobacz też

[\<ciąg >](../standard-library/string.md)

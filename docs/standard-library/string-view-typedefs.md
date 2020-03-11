---
title: '&lt;string_view&gt; Typedefs'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: c3367afe1353ac70abb74a59658a255614ac8470
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865850"
---
# <a name="ltstring_viewgt-typedefs"></a>&lt;string_view&gt; Typedefs

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a>string_view

Typ, który opisuje specjalizację szablonu klasy [basic_string_view](../standard-library/basic-string-view-class.md) z elementami typu **char**.

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>Uwagi

Poniżej przedstawiono równoważne deklaracje:

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

Aby zapoznać się z listą konstruktorów ciągów, zobacz [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string_view"></a>u16string_view

Typ, który opisuje specjalizację szablonu klasy [basic_string_view](../standard-library/basic-string-view-class.md) z elementami typu `char16_t`.

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>Uwagi

Aby zapoznać się z listą konstruktorów ciągów, zobacz [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string_view"></a>u32string_view

Typ, który opisuje specjalizację szablonu klasy [basic_string_view](../standard-library/basic-string-view-class.md) z elementami typu `char32_t`.

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>Uwagi

Aby zapoznać się z listą konstruktorów ciągów, zobacz [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring_view"></a>wstring_view

Typ, który opisuje specjalizację szablonu klasy [basic_string_view](../standard-library/basic-string-view-class.md) z elementami typu **wchar_t**.

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>Uwagi

Poniżej przedstawiono równoważne deklaracje:

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

Aby zapoznać się z listą konstruktorów ciągów, zobacz [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Rozmiar **wchar_t** to dwie bajty w systemie Windows, ale nie jest to konieczne w przypadku wszystkich platform. Jeśli potrzebujesz string_view typu dwubajtowego o szerokości, która ma być taka sama na wszystkich platformach, użyj [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) lub [u32string_view](../standard-library/string-view-typedefs.md#u32string_view).

## <a name="see-also"></a>Zobacz także

[\<string_view >](../standard-library/string-view.md)

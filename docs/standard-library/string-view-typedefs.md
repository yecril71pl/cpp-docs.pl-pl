---
title: '&lt;string_view&gt; typedefs'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 0ec278484b7c1c9887771f6cbe7e5d0b05205dd7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376674"
---
# <a name="ltstring_viewgt-typedefs"></a>&lt;string_view&gt; typedefs

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a><a name="string_view"></a>string_view

Typ opisujący specjalizację szablonu klasy [basic_string_view](../standard-library/basic-string-view-class.md) z elementami typu **char**.

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>Uwagi

Są to równoważne deklaracje:

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

Aby uzyskać listę konstruktorów ciągów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string_view"></a><a name="u16string_view"></a>u16string_view

Typ opisujący specjalizację szablonu klasy [basic_string_view](../standard-library/basic-string-view-class.md) z `char16_t`elementami typu .

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać listę konstruktorów ciągów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string_view"></a><a name="u32string_view"></a>u32string_view

Typ opisujący specjalizację szablonu klasy [basic_string_view](../standard-library/basic-string-view-class.md) z `char32_t`elementami typu .

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać listę konstruktorów ciągów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring_view"></a><a name="wstring_view"></a>wstring_view

Typ opisujący specjalizację szablonu klasy [basic_string_view](../standard-library/basic-string-view-class.md) z elementami **typu wchar_t**.

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>Uwagi

Są to równoważne deklaracje:

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

Aby uzyskać listę konstruktorów ciągów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Rozmiar **wchar_t** jest dwa bajty w systemie Windows, ale nie jest to koniecznie w przypadku wszystkich platform. Jeśli potrzebujesz string_view szerokiego typu znaku o szerokości, która na pewno pozostanie taka sama na wszystkich platformach, użyj [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) lub [u32string_view](../standard-library/string-view-typedefs.md#u32string_view).

## <a name="see-also"></a>Zobacz też

[\<string_view>](../standard-library/string-view.md)

---
title: '&lt;string_view&gt; definicje typów'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 16d7ba49facf24dcffb7df444e445d83d92255e0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346645"
---
# <a name="ltstringviewgt-typedefs"></a>&lt;string_view&gt; definicje typów

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a> string_view

Typ, który opisuje specjalizacji szablonu klasy [basic_string_view](../standard-library/basic-string-view-class.md) elementami typu **char**.

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>Uwagi

Równoważne deklaracji są następujące:

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

Aby uzyskać listę parametrów konstruktorów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string_view"></a> u16string_view

Typ, który opisuje specjalizacji szablonu klasy [basic_string_view](../standard-library/basic-string-view-class.md) elementami typu `char16_t`.

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać listę parametrów konstruktorów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string_view"></a> u32string_view

Typ, który opisuje specjalizacji szablonu klasy [basic_string_view](../standard-library/basic-string-view-class.md) elementami typu `char32_t`.

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać listę parametrów konstruktorów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring_view"></a>  wstring_view

Typ, który opisuje specjalizacji szablonu klasy [basic_string_view](../standard-library/basic-string-view-class.md) elementami typu **wchar_t**.

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>Uwagi

Równoważne deklaracji są następujące:

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

Aby uzyskać listę parametrów konstruktorów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Rozmiar **wchar_t** dwóch bajtów na Windows, ale nie jest wymagane dla wszystkich platform. Jeśli potrzebujesz typu znaku dwubajtowego string_view o szerokości, który gwarantuje pozostają takie same na wszystkich platformach, należy użyć [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) lub [u32string_view](../standard-library/string-view-typedefs.md#u32string_view).

## <a name="see-also"></a>Zobacz także

[\<string_view >](../standard-library/string-view.md)<br/>

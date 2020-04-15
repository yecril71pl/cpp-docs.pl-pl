---
title: '&lt;typedefs ciąg&gt;'
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 1ee36d67d137c74e17fff845f9d412b2673f311e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376639"
---
# <a name="ltstringgt-typedefs"></a>&lt;typedefs ciąg&gt;

||||
|-|-|-|
|[Ciąg](#string)|[u16string](#u16string)|[u32string](#u32string)|
|[wstręt](#wstring)|

## <a name="string"></a><a name="string"></a>Ciąg

Typ opisujący specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) z elementami typu **char**.

Inne typedefs, `basic_string` które specjalizują się to [wstring](../standard-library/string-typedefs.md#wstring), [u16string](../standard-library/string-typedefs.md#u16string)i [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>Uwagi

Są to równoważne deklaracje:

```cpp
string str("");

basic_string<char> str("");
```

Aby uzyskać listę konstruktorów ciągów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string"></a><a name="u16string"></a>u16string

Typ opisujący specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) z `char16_t`elementami typu .

Inne typedefs, `basic_string` które specjalizują się to [wstring](../standard-library/string-typedefs.md#wstring), [string](../standard-library/string-typedefs.md#string)i [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać listę konstruktorów ciągów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string"></a><a name="u32string"></a>u32string

Typ opisujący specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) z `char32_t`elementami typu .

Inne typedefs, `basic_string` które specjalizują się to [ciąg](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)i [wstring](../standard-library/string-typedefs.md#wstring).

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać listę konstruktorów ciągów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring"></a><a name="wstring"></a>wstręt

Typ opisujący specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) z elementami **typu wchar_t**.

Inne typedefs, `basic_string` które specjalizują się to [ciąg](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)i [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>Uwagi

Są to równoważne deklaracje:

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

Aby uzyskać listę konstruktorów ciągów, zobacz [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Rozmiar **wchar_t** jest zdefiniowany w implementacji. Jeśli kod zależy od **tego, wchar_t** ma określony rozmiar, sprawdź implementację `sizeof(wchar_t)`platformy (na przykład za pomocą ). Jeśli potrzebujesz typu znaku ciągu o szerokości, która ma być taka sama na wszystkich platformach, użyj [ciągu](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string)lub [u32string](../standard-library/string-typedefs.md#u32string).

## <a name="see-also"></a>Zobacz też

[\<>ciągu](../standard-library/string.md)

---
title: '&lt;regex&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- regex/std::cmatch
- regex/std::cregex_iterator
- regex/std::cregex_token_iterator
- regex/std::csub_match
- regex/std::regex
- regex/std::smatch
- regex/std::sregex_iterator
- regex/std::sregex_token_iterator
- regex/std::ssub_match
- regex/std::wcmatch
- regex/std::wcregex_iterator
- regex/std::wcregex_token_iterator
- regex/std::wcsub_match
- regex/std::wregex
- regex/std::wsmatch
- regex/std::wsregex_iterator
- regex/std::wsregex_token_iterator
- regex/std::wssub_match
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
ms.openlocfilehash: 5dbda2df4877da7594dd633e9f203a3780b4adb1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368545"
---
# <a name="ltregexgt-typedefs"></a>&lt;regex&gt; typedefs

||||
|-|-|-|
|[cmatch (polski)](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|
|[csub_match](#csub_match)|[Regex](#regex)|[smatch (smatch)](#smatch)|
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|
|[wcmatch](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|
|[wcsub_match](#wcsub_match)|[wregex](#wregex)|[wsmatch](#wsmatch)|
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|

## <a name="cmatch-typedef"></a><a name="cmatch"></a>cmatch Typedef

Definicja typu dla match_results char.

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [match_results Class](../standard-library/match-results-class.md) dla iteratorów typu `const char*`.

## <a name="cregex_iterator-typedef"></a><a name="cregex_iterator"></a>cregex_iterator Typedef

Definicja typu dla regex_iterator char.

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [regex_iterator Class](../standard-library/regex-iterator-class.md) dla `const char*`iteratorów typu .

## <a name="cregex_token_iterator-typedef"></a><a name="cregex_token_iterator"></a>cregex_token_iterator Typedef

Definicja typu dla regex_token_iterator znak

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [regex_token_iterator Class](../standard-library/regex-token-iterator-class.md) dla iteratorów typu `const char*`.

## <a name="csub_match-typedef"></a><a name="csub_match"></a>csub_match Typedef

Definicja typu dla sub_match char.

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [sub_match Class](../standard-library/sub-match-class.md) dla iteratorów typu `const char*`.

## <a name="regex-typedef"></a><a name="regex"></a>regex Typedef

Definicja typu dla basic_regex char.

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [basic_regex Class](../standard-library/basic-regex-class.md) dla elementów typu **char**.

> [!NOTE]
> Postacie wysoko bitowe będą `regex`miały nieprzewidywalne wyniki z . Wartości spoza zakresu od 0 do 127 może spowodować niezdefiniowane zachowanie.

## <a name="smatch-typedef"></a><a name="smatch"></a>smatch Typedef

Definicja typu dla match_results ciągu.

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [match_results Class](../standard-library/match-results-class.md) dla iteratorów typu `string::const_iterator`.

## <a name="sregex_iterator-typedef"></a><a name="sregex_iterator"></a>sregex_iterator Typedef

Definicja typu dla regex_iterator ciągu.

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [regex_iterator Class](../standard-library/regex-iterator-class.md) dla `string::const_iterator`iteratorów typu .

## <a name="sregex_token_iterator-typedef"></a><a name="sregex_token_iterator"></a>sregex_token_iterator Typedef

Definicja typu dla regex_token_iterator ciągu.

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [regex_token_iterator Class](../standard-library/regex-token-iterator-class.md) dla iteratorów typu `string::const_iterator`.

## <a name="ssub_match-typedef"></a><a name="ssub_match"></a>ssub_match Typedef

Definicja typu dla sub_match ciągu.

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [sub_match Class](../standard-library/sub-match-class.md) dla iteratorów typu `string::const_iterator`.

## <a name="wcmatch-typedef"></a><a name="wcmatch"></a>wcmatch Typedef

Definicja typu match_results wchar_t.

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [match_results Class](../standard-library/match-results-class.md) dla iteratorów typu `const wchar_t*`.

## <a name="wcregex_iterator-typedef"></a><a name="wcregex_iterator"></a>wcregex_iterator Typedef

Definicja typu regex_iterator wchar_t.

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [regex_iterator Class](../standard-library/regex-iterator-class.md) dla `const wchar_t*`iteratorów typu .

## <a name="wcregex_token_iterator-typedef"></a><a name="wcregex_token_iterator"></a>wcregex_token_iterator Typedef

Definicja typu regex_token_iterator wchar_t.

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [regex_token_iterator Class](../standard-library/regex-token-iterator-class.md) dla iteratorów typu `const wchar_t*`.

## <a name="wcsub_match-typedef"></a><a name="wcsub_match"></a>wcsub_match Typedef

Definicja typu wchar_t sub_match.

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [sub_match Class](../standard-library/sub-match-class.md) dla iteratorów typu `const wchar_t*`.

## <a name="wregex-typedef"></a><a name="wregex"></a>wregex Typedef

Definicja typu basic_regex wchar_t.

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [basic_regex Class](../standard-library/basic-regex-class.md) dla elementów **typu wchar_t**.

## <a name="wsmatch-typedef"></a><a name="wsmatch"></a>wsmatch Typedef

Definicja typu dla match_results wstringu.

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [match_results Class](../standard-library/match-results-class.md) dla iteratorów typu `wstring::const_iterator`.

## <a name="wsregex_iterator-typedef"></a><a name="wsregex_iterator"></a>wsregex_iterator Typedef

Definicja typu dla regex_iterator wstringu.

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [regex_iterator Class](../standard-library/regex-iterator-class.md) dla `wstring::const_iterator`iteratorów typu .

## <a name="wsregex_token_iterator-typedef"></a><a name="wsregex_token_iterator"></a>wsregex_token_iterator Typedef

Definicja typu dla regex_token_iterator wstringu.

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [regex_token_iterator Class](../standard-library/regex-token-iterator-class.md) dla iteratorów typu `wstring::const_iterator`.

## <a name="wssub_match-typedef"></a><a name="wssub_match"></a>wssub_match Typedef

Definicja typu dla sub_match wstringu.

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [sub_match Class](../standard-library/sub-match-class.md) dla iteratorów typu `wstring::const_iterator`.

## <a name="see-also"></a>Zobacz też

[\<>regex](../standard-library/regex.md)\
[Klasa regex_constants](../standard-library/regex-constants-class.md)\
[Klasa regex_error](../standard-library/regex-error-class.md)\
[\<funkcje> regex](../standard-library/regex-functions.md)\
[Klasa regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operatorzy> regex](../standard-library/regex-operators.md)\
[Klasa regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[regex_traits — Klasa](../standard-library/regex-traits-class.md)

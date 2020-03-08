---
title: '&lt;wyrażenie regularne&gt; Typedefs'
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
ms.openlocfilehash: 4321d9ea6fd9ba57074b25e084553fe1f0846213
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876147"
---
# <a name="ltregexgt-typedefs"></a>&lt;wyrażenie regularne&gt; Typedefs

||||
|-|-|-|
|[cmatch —](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|
|[csub_match](#csub_match)|[wyrażeń](#regex)|[Smatch —](#smatch)|
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|
|[wcmatch —](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|
|[wcsub_match](#wcsub_match)|[wRegex —](#wregex)|[wsmatch —](#wsmatch)|
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|

## <a name="cmatch"></a>cmatch — typedef

Definicja typu dla znaku match_results.

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Match_results klasy](../standard-library/match-results-class.md) dla iteratorów typu `const char*`.

## <a name="cregex_iterator"></a>cregex_iterator typedef

Definicja typu dla znaku regex_iterator.

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Regex_iterator klasy](../standard-library/regex-iterator-class.md) dla iteratorów typu `const char*`.

## <a name="cregex_token_iterator"></a>cregex_token_iterator typedef

Definicja typu dla znaku regex_token_iterator

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Regex_token_iterator klasy](../standard-library/regex-token-iterator-class.md) dla iteratorów typu `const char*`.

## <a name="csub_match"></a>csub_match typedef

Definicja typu dla znaku sub_match.

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Sub_match klasy](../standard-library/sub-match-class.md) dla iteratorów typu `const char*`.

## <a name="regex"></a>wyrażenie regularne — typedef

Definicja typu dla znaku basic_regex.

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Basic_regex klasy](../standard-library/basic-regex-class.md) dla elementów typu **char**.

> [!NOTE]
> Znaki o dużej wartości bitowej będą mieć nieprzewidywalne wyniki z `regex`. Wartości spoza zakresu od 0 do 127 mogą spowodować niezdefiniowane zachowanie.

## <a name="smatch"></a>Smatch — typedef

Definicja typu dla match_results ciągu.

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Match_results klasy](../standard-library/match-results-class.md) dla iteratorów typu `string::const_iterator`.

## <a name="sregex_iterator"></a>sregex_iterator typedef

Definicja typu dla regex_iterator ciągu.

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Regex_iterator klasy](../standard-library/regex-iterator-class.md) dla iteratorów typu `string::const_iterator`.

## <a name="sregex_token_iterator"></a>sregex_token_iterator typedef

Definicja typu dla regex_token_iterator ciągu.

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Regex_token_iterator klasy](../standard-library/regex-token-iterator-class.md) dla iteratorów typu `string::const_iterator`.

## <a name="ssub_match"></a>ssub_match typedef

Definicja typu dla sub_match ciągu.

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Sub_match klasy](../standard-library/sub-match-class.md) dla iteratorów typu `string::const_iterator`.

## <a name="wcmatch"></a>wcmatch — typedef

Definicja typu wchar_t match_results.

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Match_results klasy](../standard-library/match-results-class.md) dla iteratorów typu `const wchar_t*`.

## <a name="wcregex_iterator"></a>wcregex_iterator typedef

Definicja typu wchar_t regex_iterator.

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Regex_iterator klasy](../standard-library/regex-iterator-class.md) dla iteratorów typu `const wchar_t*`.

## <a name="wcregex_token_iterator"></a>wcregex_token_iterator typedef

Definicja typu wchar_t regex_token_iterator.

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Regex_token_iterator klasy](../standard-library/regex-token-iterator-class.md) dla iteratorów typu `const wchar_t*`.

## <a name="wcsub_match"></a>wcsub_match typedef

Definicja typu wchar_t sub_match.

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Sub_match klasy](../standard-library/sub-match-class.md) dla iteratorów typu `const wchar_t*`.

## <a name="wregex"></a>wRegex — typedef

Definicja typu wchar_t basic_regex.

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Basic_regex klasy](../standard-library/basic-regex-class.md) dla elementów typu **wchar_t**.

## <a name="wsmatch"></a>wsmatch — typedef

Definicja typu dla wstring match_results.

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Match_results klasy](../standard-library/match-results-class.md) dla iteratorów typu `wstring::const_iterator`.

## <a name="wsregex_iterator"></a>wsregex_iterator typedef

Definicja typu dla wstring regex_iterator.

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Regex_iterator klasy](../standard-library/regex-iterator-class.md) dla iteratorów typu `wstring::const_iterator`.

## <a name="wsregex_token_iterator"></a>wsregex_token_iterator typedef

Definicja typu dla wstring regex_token_iterator.

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Regex_token_iterator klasy](../standard-library/regex-token-iterator-class.md) dla iteratorów typu `wstring::const_iterator`.

## <a name="wssub_match"></a>wssub_match typedef

Definicja typu dla wstring sub_match.

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [Sub_match klasy](../standard-library/sub-match-class.md) dla iteratorów typu `wstring::const_iterator`.

## <a name="see-also"></a>Zobacz też

[\<> wyrażeń regularnych](../standard-library/regex.md)\
\ [klasy regex_constants](../standard-library/regex-constants-class.md)
\ [klasy regex_error](../standard-library/regex-error-class.md)
[\<funkcje > wyrażeń regularnych](../standard-library/regex-functions.md)\
\ [klasy regex_iterator](../standard-library/regex-iterator-class.md)
[\<operatory wyrażeń regularnych >](../standard-library/regex-operators.md)\
\ [klasy regex_token_iterator](../standard-library/regex-token-iterator-class.md)
[regex_traits, klasa](../standard-library/regex-traits-class.md)

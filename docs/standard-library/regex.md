---
title: '&lt;regex &gt;'
ms.date: 11/04/2016
f1_keywords:
- <regex>
helpviewer_keywords:
- regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
ms.openlocfilehash: 69adc738d5af3de5997e01c0f861400eb61f1712
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686588"
---
# <a name="ltregexgt"></a>&lt;regex &gt;

Definiuje szablon klasy w celu przeanalizowania [wyrażeńC++regularnych ()](../standard-library/regular-expressions-cpp.md)i kilku szablonów klas i funkcji w celu przeszukania tekstu w celu dopasowania do obiektu wyrażenia regularnego.

## <a name="syntax"></a>Składnia

```cpp
#include <regex>
```

## <a name="remarks"></a>Uwagi

Aby utworzyć obiekt wyrażenia regularnego, należy użyć [klasy basic_regex](../standard-library/basic-regex-class.md) szablonu klasy lub jednej z jej specjalizacji, [wyrażenia regularnego](../standard-library/regex-typedefs.md#regex) i [wRegex —](../standard-library/regex-typedefs.md#wregex), a także flag składni typu [regex_constants:: syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

Aby wyszukać dopasowania do obiektu wyrażenia regularnego, użyj funkcji szablonu [regex_match](../standard-library/regex-functions.md#regex_match) i [regex_search](../standard-library/regex-functions.md#regex_search), a także flag dopasowania typu [regex_constants:: match_flag_type](../standard-library/regex-constants-class.md#match_flag_type). Te funkcje zwracają wyniki przy użyciu [klasy match_results](../standard-library/match-results-class.md) szablonu klasy i jej specjalizacji, [cmatch —](../standard-library/regex-typedefs.md#cmatch), [wcmatch —](../standard-library/regex-typedefs.md#wcmatch), [Smatch —](../standard-library/regex-typedefs.md#smatch)i [wsmatch —](../standard-library/regex-typedefs.md#wsmatch), a także z [klasą sub_match](../standard-library/sub-match-class.md) szablonu klasy i jej Specjalizacje, [csub_match](../standard-library/regex-typedefs.md#csub_match), [wcsub_match](../standard-library/regex-typedefs.md#wcsub_match), [ssub_match](../standard-library/regex-typedefs.md#ssub_match)i [wssub_match](../standard-library/regex-typedefs.md#wssub_match).

Aby zamienić tekst, który pasuje do obiektu wyrażenia regularnego, użyj funkcji template [regex_replace](../standard-library/regex-functions.md#regex_replace)wraz z flagami dopasowania typu [regex_constants:: match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).

Aby wykonać iterację wielu dopasowań obiektu wyrażenia regularnego, należy użyć szablonów klas [Regex_iterator klasy](../standard-library/regex-iterator-class.md) i [klasy regex_token_iterator](../standard-library/regex-token-iterator-class.md) lub jednej z ich specjalizacji, [cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator), [sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator), [ wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator), [wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator), [cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator), [sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator), [wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator)lub [wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator), wraz z flagami dopasowania typu [regex_ stałe:: match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).

Aby zmodyfikować szczegóły dotyczące gramatyki wyrażeń regularnych, należy napisać klasę, która implementuje cechy wyrażenia regularnego.

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_regex](../standard-library/basic-regex-class.md)|Owija wyrażenie regularne.|
|[match_results](../standard-library/match-results-class.md)|Przechowuje sekwencję podpasowań.|
|[regex_constants](../standard-library/regex-constants-class.md)|Przechowuje stałe.|
|[regex_error](../standard-library/regex-error-class.md)|Zgłasza nieprawidłowe wyrażenie regularne.|
|[regex_iterator](../standard-library/regex-iterator-class.md)|Wykonuje iterację w wyniku dopasowania.|
|[regex_traits](../standard-library/regex-traits-class.md)|Opisuje charakterystykę elementów do dopasowania.|
|[regex_traits \<char >](../standard-library/regex-traits-char-class.md)|Opisuje charakterystykę **char** do dopasowania.|
|[regex_traits < wchar_t >](../standard-library/regex-traits-wchar-t-class.md)|Opisuje charakterystykę **wchar_t** do dopasowania.|
|[regex_token_iterator](../standard-library/regex-token-iterator-class.md)|Wykonuje iterację przez poddopasowania.|
|[sub_match](../standard-library/sub-match-class.md)|Opisuje poddopasowanie.|

### <a name="type-definitions"></a>Definicje typu

|||
|-|-|
|[cmatch —](../standard-library/regex-typedefs.md#cmatch)|Definicja typu dla **znaku** `match_results`.|
|[cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)|Definicja typu dla **znaku** `regex_iterator`.|
|[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator)|Definicja typu dla **znaku** `regex_token_iterator`.|
|[csub_match](../standard-library/regex-typedefs.md#csub_match)|Definicja typu dla **znaku** `sub_match`.|
|[wyrażeń](../standard-library/regex-typedefs.md#regex)|Definicja typu dla **znaku** `basic_regex`.|
|[Smatch —](../standard-library/regex-typedefs.md#smatch)|Definicja typu `string` `match_results`.|
|[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)|Definicja typu `string` `regex_iterator`.|
|[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)|Definicja typu `string` `regex_token_iterator`.|
|[ssub_match](../standard-library/regex-typedefs.md#ssub_match)|Definicja typu `string` `sub_match`.|
|[wcmatch —](../standard-library/regex-typedefs.md#wcmatch)|Definicja typu dla **wchar_t** `match_results`.|
|[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)|Definicja typu dla **wchar_t** `regex_iterator`.|
|[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator)|Definicja typu dla **wchar_t** `regex_token_iterator`.|
|[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)|Definicja typu dla **wchar_t** `sub_match`.|
|[wRegex —](../standard-library/regex-typedefs.md#wregex)|Definicja typu dla **wchar_t** `basic_regex`.|
|[wsmatch —](../standard-library/regex-typedefs.md#wsmatch)|Definicja typu `wstring` `match_results`.|
|[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator)|Definicja typu `wstring` `regex_iterator`.|
|[wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator)|Definicja typu `wstring` `regex_token_iterator`.|
|[wssub_match](../standard-library/regex-typedefs.md#wssub_match)|Definicja typu `wstring` `sub_match`.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[regex_match](../standard-library/regex-functions.md#regex_match)|Dokładnie pasuje do wyrażenia regularnego.|
|[regex_replace](../standard-library/regex-functions.md#regex_replace)|Zastępuje dopasowane wyrażenia regularne.|
|[regex_search](../standard-library/regex-functions.md#regex_search)|Wyszukuje dopasowanie wyrażenia regularnego.|
|[wymiany](../standard-library/regex-functions.md#swap)|Zamienia obiekty `basic_regex` lub `match_results`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator = =](../standard-library/regex-operators.md#op_eq_eq)|Porównanie różnych obiektów, równe.|
|[operator!=](../standard-library/regex-operators.md#op_neq)|Porównanie różnych obiektów, a nie równa się.|
|[< operatora](../standard-library/regex-operators.md#op_lt)|Porównanie różnych obiektów, mniejsze niż.|
|[\< operatora =](../standard-library/regex-operators.md#op_gt_eq)|Porównanie różnych obiektów, mniejszej lub równej.|
|[> operatora](../standard-library/regex-operators.md#op_gt)|Porównanie różnych obiektów, większe niż.|
|[operator>=](../standard-library/regex-operators.md#op_gt_eq)|Porównanie różnych obiektów, większe niż lub równe.|
|[< operatora <](../standard-library/regex-operators.md#op_lt_lt)|Wstawia `sub_match` w strumieniu.|

## <a name="see-also"></a>Zobacz także

[Wyrażenia regularne (C++)](../standard-library/regular-expressions-cpp.md) \
[Klasa regex_constants](../standard-library/regex-constants-class.md) \
[Klasa regex_error](../standard-library/regex-error-class.md) \
[\<regex funkcje >](../standard-library/regex-functions.md) \
[Klasa regex_iterator](../standard-library/regex-iterator-class.md) \
[\<regex operatory >](../standard-library/regex-operators.md) \
[Klasa regex_token_iterator](../standard-library/regex-token-iterator-class.md) \
[Klasa regex_traits](../standard-library/regex-traits-class.md) \
[\<regex > Typedefs](../standard-library/regex-typedefs.md)

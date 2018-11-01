---
title: '&lt;regex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <regex>
helpviewer_keywords:
- regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
ms.openlocfilehash: 0a4728008130119ed9a01334efb2fea2a4ac0639
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627347"
---
# <a name="ltregexgt"></a>&lt;regex&gt;

Definiuje klasę szablonu, można przeanalizować [wyrażenia regularne (C++)](../standard-library/regular-expressions-cpp.md)oraz kilka klas szablonów i funkcji do wyszukiwania tekstu dopasowania do obiektu będącego wyrażeniem regularnym.

## <a name="syntax"></a>Składnia

```cpp
#include <regex>
```

## <a name="remarks"></a>Uwagi

Aby utworzyć obiekt będący wyrażeniem regularnym, użyj klasy szablonu [basic_regex — klasa](../standard-library/basic-regex-class.md) lub jeden z jego specjalizacji [wyrażenia regularnego](../standard-library/regex-typedefs.md#regex) i [wregex](../standard-library/regex-typedefs.md#wregex), wraz z flagami składni Typ [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

Aby wyszukać tekst dopasowania do obiektu będącego wyrażeniem regularnym, należy użyć funkcji szablonu [regex_match —](../standard-library/regex-functions.md#regex_match) i [regex_search —](../standard-library/regex-functions.md#regex_search), wraz z użyciem flag dopasowanie typu [regex_constants::match_ flag_type](../standard-library/regex-constants-class.md#match_flag_type). Te funkcje zwracają wyniki za pomocą klasy szablonu [match_results, klasa](../standard-library/match-results-class.md) i jego specjalizacji [cmatch](../standard-library/regex-typedefs.md#cmatch), [wcmatch](../standard-library/regex-typedefs.md#wcmatch), [smatch](../standard-library/regex-typedefs.md#smatch), i [wsmatch](../standard-library/regex-typedefs.md#wsmatch), wraz z klasą szablonu [sub_match, klasa](../standard-library/sub-match-class.md) i jego specjalizacji [csub_match](../standard-library/regex-typedefs.md#csub_match), [wcsub_ odpowiada](../standard-library/regex-typedefs.md#wcsub_match), [ssub_match](../standard-library/regex-typedefs.md#ssub_match), i [wssub_match](../standard-library/regex-typedefs.md#wssub_match).

Aby zamienić tekst, który odpowiada obiektu będącego wyrażeniem regularnym, należy użyć funkcji szablonu [regex_replace —](../standard-library/regex-functions.md#regex_replace), wraz z użyciem flag dopasowanie typu [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).

Do iteracji przez wiele dopasowań obiektu będącego wyrażeniem regularnym, należy użyć klas szablonów [regex_iterator, klasa](../standard-library/regex-iterator-class.md) i [regex_token_iterator, klasa](../standard-library/regex-token-iterator-class.md) lub jednej z ich specjalizacje [ cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator), [sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator), [wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator), [wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator), [cregex_token_iterator ](../standard-library/regex-typedefs.md#cregex_token_iterator), [sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator), [wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator), lub [wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator), wraz z użyciem flag dopasowanie typu [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).

Aby zmodyfikować szczegóły gramatyki wyrażeń regularnych, należy napisać klasę, która implementuje cechy wyrażeń regularnych.

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_regex](../standard-library/basic-regex-class.md)|Owija wyrażenie regularne.|
|[match_results](../standard-library/match-results-class.md)|Zawiera sekwencję poddopasowania.|
|[regex_constants](../standard-library/regex-constants-class.md)|Stałe są formatowane przy blokad.|
|[regex_error](../standard-library/regex-error-class.md)|Zgłasza zły wyrażenia regularnego.|
|[regex_iterator](../standard-library/regex-iterator-class.md)|Wykonuje iterację przez dopasowanie wyników.|
|[regex_traits](../standard-library/regex-traits-class.md)|Zawiera opis właściwości elementów do dopasowania.|
|[regex_traits\<char >](../standard-library/regex-traits-char-class.md)|W tym artykule opisano charakterystyki **char** do dopasowania.|
|[regex_traits < wchar_t >](../standard-library/regex-traits-wchar-t-class.md)|W tym artykule opisano charakterystyki **wchar_t** do dopasowania.|
|[regex_token_iterator](../standard-library/regex-token-iterator-class.md)|Wykonuje iterację przez poddopasowania.|
|[sub_match](../standard-library/sub-match-class.md)|W tym artykule opisano poddopasowanie.|

### <a name="type-definitions"></a>Definicje typów

|||
|-|-|
|[cmatch](../standard-library/regex-typedefs.md#cmatch)|Wpisz definicję dla **char** `match_results`.|
|[cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)|Wpisz definicję dla **char** `regex_iterator`.|
|[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator)|Wpisz definicję dla **char** `regex_token_iterator`.|
|[csub_match](../standard-library/regex-typedefs.md#csub_match)|Wpisz definicję dla **char** `sub_match`.|
|[regex](../standard-library/regex-typedefs.md#regex)|Wpisz definicję dla **char** `basic_regex`.|
|[smatch](../standard-library/regex-typedefs.md#smatch)|Wpisz definicję dla `string` `match_results`.|
|[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)|Wpisz definicję dla `string` `regex_iterator`.|
|[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)|Wpisz definicję dla `string` `regex_token_iterator`.|
|[ssub_match](../standard-library/regex-typedefs.md#ssub_match)|Wpisz definicję dla `string` `sub_match`.|
|[wcmatch](../standard-library/regex-typedefs.md#wcmatch)|Wpisz definicję dla **wchar_t** `match_results`.|
|[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)|Wpisz definicję dla **wchar_t** `regex_iterator`.|
|[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator)|Wpisz definicję dla **wchar_t** `regex_token_iterator`.|
|[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)|Wpisz definicję dla **wchar_t** `sub_match`.|
|[wregex](../standard-library/regex-typedefs.md#wregex)|Wpisz definicję dla **wchar_t** `basic_regex`.|
|[wsmatch](../standard-library/regex-typedefs.md#wsmatch)|Wpisz definicję dla `wstring` `match_results`.|
|[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator)|Wpisz definicję dla `wstring` `regex_iterator`.|
|[wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator)|Wpisz definicję dla `wstring` `regex_token_iterator`.|
|[wssub_match](../standard-library/regex-typedefs.md#wssub_match)|Wpisz definicję dla `wstring` `sub_match`.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[regex_match](../standard-library/regex-functions.md#regex_match)|Dokładnie pasuje do wyrażenia regularnego.|
|[regex_replace](../standard-library/regex-functions.md#regex_replace)|Zamienia dopasowany wyrażeń regularnych.|
|[regex_search](../standard-library/regex-functions.md#regex_search)|Wyszukuje dopasowania wyrażenia regularnego.|
|[swap](../standard-library/regex-functions.md#swap)|Zamienia `basic_regex` lub `match_results` obiektów.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator==](../standard-library/regex-operators.md#op_eq_eq)|Porównanie różnych obiektów, taki sam.|
|[operator!=](../standard-library/regex-operators.md#op_neq)|Porównanie różnych obiektów, nie równa się.|
|[Operator <](../standard-library/regex-operators.md#op_lt)|Porównanie różnych obiektów, poniżej.|
|[Operator\<=](../standard-library/regex-operators.md#op_gt_eq)|Porównanie różnych obiektów, mniejsze niż lub równe.|
|[operator>](../standard-library/regex-operators.md#op_gt)|Porównanie różnych obiektów, większa.|
|[operator>=](../standard-library/regex-operators.md#op_gt_eq)|Porównanie różnych obiektów, większe niż lub równe.|
|[Operator <<](../standard-library/regex-operators.md#op_lt_lt)|Wstawia `sub_match` w strumieniu.|

## <a name="see-also"></a>Zobacz także

[Wyrażenia regularne (C++)](../standard-library/regular-expressions-cpp.md)<br/>
[regex_constants, klasa](../standard-library/regex-constants-class.md)<br/>
[regex_error, klasa](../standard-library/regex-error-class.md)<br/>
[\<wyrażenie regularne > funkcji](../standard-library/regex-functions.md)<br/>
[regex_iterator, klasa](../standard-library/regex-iterator-class.md)<br/>
[\<wyrażenie regularne > operatorów](../standard-library/regex-operators.md)<br/>
[regex_token_iterator, klasa](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits, klasa](../standard-library/regex-traits-class.md)<br/>
[\<wyrażenie regularne > definicje typów](../standard-library/regex-typedefs.md)<br/>

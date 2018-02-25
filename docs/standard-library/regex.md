---
title: '&lt;regex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <regex>
dev_langs:
- C++
helpviewer_keywords:
- regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c586cf909ce07f17dfdba08005d1efd8489db869
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltregexgt"></a>&lt;regex&gt;
Definiuje klasę szablonu, aby przeanalizować [wyrażenia regularne (C++)](../standard-library/regular-expressions-cpp.md)oraz kilka klas szablonów i funkcji do wyszukiwania tekstu pasuje do obiektu będącego wyrażeniem regularnym.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <regex>  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć obiekt będący wyrażeniem regularnym, użyj klasy szablonu [basic_regex — klasa](../standard-library/basic-regex-class.md) lub jednego z jego specjalizacje [regex](../standard-library/regex-typedefs.md#regex) i [wregex](../standard-library/regex-typedefs.md#wregex), wraz z flagami składni Typ [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).  
  
 Do wyszukiwania tekstu pasuje do obiektu będącego wyrażeniem regularnym, należy użyć funkcji szablonu [regex_match —](../standard-library/regex-functions.md#regex_match) i [regex_search —](../standard-library/regex-functions.md#regex_search), wraz z flagami dopasowanie typu [regex_constants::match_ flag_type](../standard-library/regex-constants-class.md#match_flag_type). Funkcje zwracają wyniki za pomocą klasy szablonu [match_results — klasa](../standard-library/match-results-class.md) i jego specjalizacje [cmatch](../standard-library/regex-typedefs.md#cmatch), [wcmatch](../standard-library/regex-typedefs.md#wcmatch), [smatch](../standard-library/regex-typedefs.md#smatch), i [wsmatch](../standard-library/regex-typedefs.md#wsmatch), wraz z klasy szablonu [sub_match — klasa](../standard-library/sub-match-class.md) i jego specjalizacje [csub_match](../standard-library/regex-typedefs.md#csub_match), [wcsub_ odpowiada](../standard-library/regex-typedefs.md#wcsub_match), [ssub_match](../standard-library/regex-typedefs.md#ssub_match), i [wssub_match](../standard-library/regex-typedefs.md#wssub_match).  
  
 Aby zastąpić tekst, który pasuje do obiektu będącego wyrażeniem regularnym, należy użyć funkcji szablonu [regex_replace —](../standard-library/regex-functions.md#regex_replace), wraz z flagami dopasowanie typu [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).  
  
 Aby Iterowanie za pomocą wielu dopasowań obiektu będącego wyrażeniem regularnym, należy użyć klasy szablonu [regex_iterator — klasa](../standard-library/regex-iterator-class.md) i [regex_token_iterator — klasa](../standard-library/regex-token-iterator-class.md) lub jednej z ich specjalizacje [ cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator), [sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator), [wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator), [wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator), [cregex_token_iterator ](../standard-library/regex-typedefs.md#cregex_token_iterator), [sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator), [wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator), lub [wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator), wraz z flagami dopasowanie typu [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).  
  
 Aby zmodyfikować szczegóły gramatyki wyrażeń regularnych, zapisać klasy, która implementuje cech wyrażenia regularnego.  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[basic_regex](../standard-library/basic-regex-class.md)|Owija wyrażenie regularne.|  
|[match_results](../standard-library/match-results-class.md)|Zawiera sekwencję submatches.|  
|[regex_constants](../standard-library/regex-constants-class.md)|Stałe wybrane blokad.|  
|[regex_error](../standard-library/regex-error-class.md)|Raporty nieprawidłowe wyrażenie regularne.|  
|[regex_iterator](../standard-library/regex-iterator-class.md)|Wykonuje iterację dopasowania wyników.|  
|[regex_traits](../standard-library/regex-traits-class.md)|Opisuje właściwości elementów do dopasowania.|  
|[regex_traits —\<char >](../standard-library/regex-traits-char-class.md)|Opisuje właściwości `char` do dopasowania.|  
|[regex_traits<wchar_t>](../standard-library/regex-traits-wchar-t-class.md)|Opisuje właściwości `wchar_t` do dopasowania.|  
|[regex_token_iterator](../standard-library/regex-token-iterator-class.md)|Wykonuje iterację submatches.|  
|[sub_match](../standard-library/sub-match-class.md)|W tym artykule opisano submatch.|  
  
### <a name="type-definitions"></a>Definicje typów  
  
|||  
|-|-|  
|[cmatch](../standard-library/regex-typedefs.md#cmatch)|Definicji dla typu `char` `match_results`.|  
|[cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)|Definicji dla typu `char` `regex_iterator`.|  
|[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator)|Definicji dla typu `char` `regex_token_iterator`.|  
|[csub_match](../standard-library/regex-typedefs.md#csub_match)|Definicji dla typu `char` `sub_match`.|  
|[regex](../standard-library/regex-typedefs.md#regex)|Definicji dla typu `char` `basic_regex`.|  
|[smatch](../standard-library/regex-typedefs.md#smatch)|Definicji dla typu `string` `match_results`.|  
|[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)|Definicji dla typu `string` `regex_iterator`.|  
|[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)|Definicji dla typu `string` `regex_token_iterator`.|  
|[ssub_match](../standard-library/regex-typedefs.md#ssub_match)|Definicji dla typu `string` `sub_match`.|  
|[wcmatch](../standard-library/regex-typedefs.md#wcmatch)|Definicji dla typu `wchar_t` `match_results`.|  
|[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)|Definicji dla typu `wchar_t` `regex_iterator`.|  
|[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator)|Definicji dla typu `wchar_t` `regex_token_iterator`.|  
|[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)|Definicji dla typu `wchar_t` `sub_match`.|  
|[wregex](../standard-library/regex-typedefs.md#wregex)|Definicji dla typu `wchar_t` `basic_regex`.|  
|[wsmatch](../standard-library/regex-typedefs.md#wsmatch)|Definicji dla typu `wstring` `match_results`.|  
|[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator)|Definicji dla typu `wstring` `regex_iterator`.|  
|[wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator)|Definicji dla typu `wstring` `regex_token_iterator`.|  
|[wssub_match](../standard-library/regex-typedefs.md#wssub_match)|Definicji dla typu `wstring` `sub_match`.|  
  
### <a name="functions"></a>Funkcje  
  
|||  
|-|-|  
|[regex_match](../standard-library/regex-functions.md#regex_match)|Dokładnie odpowiada wyrażeniu regularnemu.|  
|[regex_replace](../standard-library/regex-functions.md#regex_replace)|Zamienia dopasowaniu wyrażenia regularne.|  
|[regex_search](../standard-library/regex-functions.md#regex_search)|Wyszukuje wyrażenie regularne zgodne.|  
|[swap](../standard-library/regex-functions.md#swap)|Zamienia `basic_regex` lub `match_results` obiektów.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator==](../standard-library/regex-operators.md#op_eq_eq)|Porównanie różnych obiektów, takie same.|  
|[operator!=](../standard-library/regex-operators.md#op_neq)|Porównanie różnych obiektów, nie jest równa.|  
|[Operator <](../standard-library/regex-operators.md#op_lt)|Porównanie różnych obiektów, poniżej.|  
|[operator\<=](../standard-library/regex-operators.md#op_gt_eq)|Porównanie różnych obiektów, co najwyżej.|  
|[operator>](../standard-library/regex-operators.md#op_gt)|Porównanie różnych obiektów, większe.|  
|[operator>=](../standard-library/regex-operators.md#op_gt_eq)|Porównanie różnych obiektów, większe lub równe.|  
|[Operator <<](../standard-library/regex-operators.md#op_lt_lt)|Wstawia `sub_match` w strumieniu.|  
  
## <a name="see-also"></a>Zobacz też  
[Wyrażenia regularne (C++)](../standard-library/regular-expressions-cpp.md)  
[regex_constants, klasa](../standard-library/regex-constants-class.md)  
[regex_error, klasa](../standard-library/regex-error-class.md)  
[\<wyrażenie regularne > Funkcje](../standard-library/regex-functions.md)  
[regex_iterator, klasa](../standard-library/regex-iterator-class.md)  
[\<wyrażenie regularne > operatory](../standard-library/regex-operators.md)  
[regex_token_iterator, klasa](../standard-library/regex-token-iterator-class.md)  
[regex_traits, klasa](../standard-library/regex-traits-class.md)  
[\<wyrażenie regularne > definicje typów](../standard-library/regex-typedefs.md)  




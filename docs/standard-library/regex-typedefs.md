---
title: "&lt;wyrażenie regularne&gt; definicje typów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7dad87e2d6e402333db5f51bdf8deaee1090df86
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltregexgt-typedefs"></a>&lt;wyrażenie regularne&gt; definicje typów
||||  
|-|-|-|  
|[cmatch](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|  
|[csub_match](#csub_match)|[wyrażenia regularnego](#regex)|[smatch](#smatch)|  
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|  
|[wcmatch](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|  
|[wcsub_match](#wcsub_match)|[wregex](#wregex)|[wsmatch](#wsmatch)|  
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|  
  
##  <a name="cmatch"></a>cmatch — Typedef  
 Typ definicji match_results — char.  
  
```  
typedef match_results<const char*> cmatch;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [match_results — klasa](../standard-library/match-results-class.md) dla Iteratory typu `const char*`.  
  
##  <a name="cregex_iterator"></a>cregex_iterator — Typedef  
 Typ definicji regex_iterator — char.  
  
```  
typedef regex_iterator<const char*> cregex_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [regex_iterator — klasa](../standard-library/regex-iterator-class.md) dla Iteratory typu `const char*`.  
  
##  <a name="cregex_token_iterator"></a>cregex_token_iterator — Typedef  
 Definicja typu char regex_token_iterator —  
  
```  
typedef regex_token_iterator<const char*> cregex_token_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [regex_token_iterator — klasa](../standard-library/regex-token-iterator-class.md) dla Iteratory typu `const char*`.  
  
##  <a name="csub_match"></a>csub_match — Typedef  
 Typ definicji sub_match — char.  
  
```  
typedef sub_match<const char*> csub_match;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [sub_match — klasa](../standard-library/sub-match-class.md) dla Iteratory typu `const char*`.  
  
##  <a name="regex"></a>regex — Typedef  
 Typ definicji basic_regex — char.  
  
```  
typedef basic_regex<char> regex;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [basic_regex — klasa](../standard-library/basic-regex-class.md) dla elementów typu `char`.  
  
> [!NOTE]
>  Znaki wysokobitowe może spowodować nieprzewidywalne skutki z `regex`. Wartości spoza zakresu od 0 do 127 znaków może spowodować niezdefiniowane zachowanie.  
  
##  <a name="smatch"></a>smatch — Typedef  
 Typ definicji match_results — ciąg.  
  
```  
typedef match_results<string::const_iterator> smatch;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [match_results — klasa](../standard-library/match-results-class.md) dla Iteratory typu `string::const_iterator`.  
  
##  <a name="sregex_iterator"></a>sregex_iterator — Typedef  
 Typ definicji regex_iterator — ciąg.  
  
```  
typedef regex_iterator<string::const_iterator> sregex_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [regex_iterator — klasa](../standard-library/regex-iterator-class.md) dla Iteratory typu `string::const_iterator`.  
  
##  <a name="sregex_token_iterator"></a>sregex_token_iterator — Typedef  
 Typ definicji regex_token_iterator — ciąg.  
  
```  
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [regex_token_iterator — klasa](../standard-library/regex-token-iterator-class.md) dla Iteratory typu `string::const_iterator`.  
  
##  <a name="ssub_match"></a>ssub_match — Typedef  
 Typ definicji sub_match — ciąg.  
  
```  
typedef sub_match<string::const_iterator> ssub_match;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [sub_match — klasa](../standard-library/sub-match-class.md) dla Iteratory typu `string::const_iterator`.  
  
##  <a name="wcmatch"></a>wcmatch — Typedef  
 Typ definicji match_results — wchar_t.  
  
```  
typedef match_results<const wchar_t *> wcmatch;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [match_results — klasa](../standard-library/match-results-class.md) dla Iteratory typu `const wchar_t*`.  
  
##  <a name="wcregex_iterator"></a>wcregex_iterator — Typedef  
 Typ definicji regex_iterator — wchar_t.  
  
```  
typedef regex_iterator<const wchar_t*> wcregex_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [regex_iterator — klasa](../standard-library/regex-iterator-class.md) dla Iteratory typu `const wchar_t*`.  
  
##  <a name="wcregex_token_iterator"></a>wcregex_token_iterator — Typedef  
 Typ definicji regex_token_iterator — wchar_t.  
  
```  
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [regex_token_iterator — klasa](../standard-library/regex-token-iterator-class.md) dla Iteratory typu `const wchar_t*`.  
  
##  <a name="wcsub_match"></a>wcsub_match — Typedef  
 Typ definicji sub_match — wchar_t.  
  
```  
typedef sub_match<const wchar_t*> wcsub_match;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [sub_match — klasa](../standard-library/sub-match-class.md) dla Iteratory typu `const wchar_t*`.  
  
##  <a name="wregex"></a>wregex — Typedef  
 Typ definicji basic_regex — wchar_t.  
  
```  
typedef basic_regex<wchar_t> wregex;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [basic_regex — klasa](../standard-library/basic-regex-class.md) dla elementów typu `wchar_t`.  
  
##  <a name="wsmatch"></a>wsmatch — Typedef  
 Typ definicji match_results wstring —.  
  
```  
typedef match_results<wstring::const_iterator> wsmatch;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [match_results — klasa](../standard-library/match-results-class.md) dla Iteratory typu `wstring::const_iterator`.  
  
##  <a name="wsregex_iterator"></a>wsregex_iterator — Typedef  
 Typ definicji regex_iterator wstring —.  
  
```  
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [regex_iterator — klasa](../standard-library/regex-iterator-class.md) dla Iteratory typu `wstring::const_iterator`.  
  
##  <a name="wsregex_token_iterator"></a>wsregex_token_iterator — Typedef  
 Typ definicji regex_token_iterator wstring —.  
  
```  
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [regex_token_iterator — klasa](../standard-library/regex-token-iterator-class.md) dla Iteratory typu `wstring::const_iterator`.  
  
##  <a name="wssub_match"></a>wssub_match — Typedef  
 Typ definicji sub_match wstring —.  
  
```  
typedef sub_match<wstring::const_iterator> wssub_match;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ w tym artykule opisano specjalizacji szablonu klasy [sub_match — klasa](../standard-library/sub-match-class.md) dla Iteratory typu `wstring::const_iterator`.  
  
## <a name="see-also"></a>Zobacz też  
[\<wyrażenie regularne >](../standard-library/regex.md)  
[regex_constants — klasa](../standard-library/regex-constants-class.md)  
[regex_error — klasa](../standard-library/regex-error-class.md)  
[\<wyrażenie regularne > Funkcje](../standard-library/regex-functions.md)  
[regex_iterator — klasa](../standard-library/regex-iterator-class.md)  
[\<wyrażenie regularne > operatory](../standard-library/regex-operators.md)  
[regex_token_iterator — klasa](../standard-library/regex-token-iterator-class.md)  
[regex_traits — klasa](../standard-library/regex-traits-class.md)  

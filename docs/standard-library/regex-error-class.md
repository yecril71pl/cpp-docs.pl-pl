---
title: "regex_error — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
dev_langs:
- C++
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1cc2861da5e133754459d6721c3ce528eaab5897
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="regexerror-class"></a>regex_error — Klasa
Raporty obiektu basic_regex — zła.  
  
## <a name="syntax"></a>Składnia  
  
```  
class regex_error  
 : public std::runtime_error {  
public:  
    explicit regex_error(regex_constants::error_code error);

    regex_constants::error_code code() const;

 
 };  
```  
  
## <a name="remarks"></a>Uwagi  
 Klasa opisuje obiekt wyjątek zgłoszony zgłosić błąd podczas konstruowania lub użycie `basic_regex` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<regex >  
  
 **Namespace:** Standard  
  
##  <a name="code"></a>  regex_error::Code  
 Zwraca kod błędu.  
  
```  
regex_constants::error_code code() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca wartość, który został przekazany do konstruktora obiektu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__regex__regex_error_code.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex_error paren(std::regex_constants::error_paren);   
  
    try   
        {   
        std::regex rx("(a");   
        }   
    catch (const std::regex_error& rerr)   
        {   
        std::cout << "regex error: "   
            << (rerr.code() == paren.code()   
                 "unbalanced parentheses" : "")   
            << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
```Output  
regex error: unbalanced parentheses  
```  
  
##  <a name="regex_error"></a>  regex_error::regex_error  
 Tworzy obiekt.  
  
```  
regex_error(regex_constants::error_code error);
```  
  
### <a name="parameters"></a>Parametry  
 `error`  
 Kod błędu.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor tworzy obiekt przechowujący wartość `error`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__regex__regex_error_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex_error paren(std::regex_constants::error_paren);   
  
    try   
        {   
        std::regex rx("(a");   
        }   
    catch (const std::regex_error& rerr)   
        {   
        std::cout << "regex error: "   
            << (rerr.code() == paren.code()   
                 "unbalanced parentheses" : "")   
            << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
```Output  
regex error: unbalanced parentheses  
```  
  
## <a name="see-also"></a>Zobacz też  
[\<regex>](../standard-library/regex.md)  
[regex_constants, klasa](../standard-library/regex-constants-class.md)  
[\<wyrażenie regularne > Funkcje](../standard-library/regex-functions.md)  
[regex_iterator, klasa](../standard-library/regex-iterator-class.md)  
[\<wyrażenie regularne > operatory](../standard-library/regex-operators.md)  
[regex_token_iterator, klasa](../standard-library/regex-token-iterator-class.md)  
[regex_traits, klasa](../standard-library/regex-traits-class.md)  
[\<wyrażenie regularne > definicje typów](../standard-library/regex-typedefs.md)  

---
title: "&lt;wyrażenie regularne&gt; operatory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex/std::operator!=
- regex/std::operator>
- regex/std::operator>=
- regex/std::operator<
- regex/std::operator<=
- regex/std::operator==
- regex/std::operator<<
dev_langs: C++
ms.assetid: ec623e65-c186-491f-aa18-6b12b47e1127
caps.latest.revision: "12"
manager: ghogen
ms.openlocfilehash: 7c37cc1a2708346ed8af0fd8b5df9a91a625feb6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltregexgt-operators"></a>&lt;wyrażenie regularne&gt; operatory
||||  
|-|-|-|  
|[operator! =](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|  
|[operator ==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>operator! =  
 Nie równa się porównania dla różnych obiektów.  
  
```  
template <class BidIt>  
bool operator!=(const sub_match<BidIt>& left,  
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>  
bool operator!=(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,  
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>  
bool operator!=(const sub_match<BidIt>& left,  
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>  
bool operator!=(const typename iterator_traits<BidIt>::value_type *left,  
    const sub_match<BidIt>& right);

template <class BidIt>  
bool operator!=(const sub_match<BidIt>& left,  
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>  
bool operator!=(const typename iterator_traits<BidIt>::value_type& left,  
    const sub_match<BidIt>& right);

template <class BidIt>  
bool operator!=(const sub_match<BidIt>& left,  
    const typename iterator_traits<BidIt>::value_type& right);

template <class BidIt, class Alloc>  
bool operator!=(const match_results<BidIt, Alloc>& left,  
    const match_results<BidIt, Alloc>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `BidIt`  
 Typ iteratora.  
  
 `IOtraits`  
 Klasa cech ciągu.  
  
 `Alloc`  
 Klasa alokatora.  
  
 `left`  
 Po lewej stronie obiekt do porównania.  
  
 `right`  
 Prawy obiekt do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca każdego szablonu operatora `!(left == right)`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__regex__operator_ne.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::cmatch::string_type Mystr;   
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "match == " << mr.str() << std::endl;   
    std::cout << "sub == " << sub << std::endl;   
    std::cout << std::endl;   
  
    std::cout << "match != match == " << std::boolalpha   
        << (mr != mr) << std::endl;   
    std::cout << "sub != sub == " << std::boolalpha   
        << (sub != sub) << std::endl;   
  
    std::cout << "string(\"aab\") != sub == " << std::boolalpha   
        << (Mystr("aab") != sub) << std::endl;   
    std::cout << "sub != string(\"aab\") == " << std::boolalpha   
        << (sub != Mystr("aab")) << std::endl;   
  
    std::cout << "\"aab\" != sub == " << std::boolalpha   
        << ("aab" != sub) << std::endl;   
    std::cout << "sub != \"aab\" == " << std::boolalpha   
        << (sub != "aab") << std::endl;   
  
    std::cout << "'a' != sub == " << std::boolalpha   
        << ('a' != sub) << std::endl;   
    std::cout << "sub != 'a' == " << std::boolalpha   
        << (sub != 'a') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == caaa  
sub == aaa  
  
match != match == false  
sub != sub == false  
string("aab") != sub == true  
sub != string("aab") == true  
"aab" != sub == true  
sub != "aab" == true  
'a' != sub == true  
sub != 'a' == true  
```  
  
##  <a name="op_lt"></a>operator&lt;  
 Mniej niż porównania dla różnych obiektów.  
  
```  
template <class BidIt>  
bool operator<(const sub_match<BidIt>& left,  
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>  
bool operator<(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,  
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>  
bool operator<(const sub_match<BidIt>& left,  
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>  
bool operator<(const typename iterator_traits<BidIt>::value_type *left,  
    const sub_match<BidIt>& right);

template <class BidIt>  
bool operator<(const sub_match<BidIt>& left,  
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>  
bool operator<(const typename iterator_traits<BidIt>::value_type& left,  
    const sub_match<BidIt>& right);

template <class BidIt>  
bool operator<(const sub_match<BidIt>& left,  
    const typename iterator_traits<BidIt>::value_type& right);
```  
  
### <a name="parameters"></a>Parametry  
 `BidIt`  
 Typ iteratora.  
  
 `IOtraits`  
 Klasa cech ciągu.  
  
 `Alloc`  
 Klasa alokatora.  
  
 `left`  
 Po lewej stronie obiekt do porównania.  
  
 `right`  
 Prawy obiekt do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Operator każdego szablonu Konwertuje argumenty typu string i zwraca wartość true tylko wtedy, gdy wartość przekonwertowanego `left` porównuje mniejsza niż wartość przekonwertowanego `right`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__regex__operator_lt.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::cmatch::string_type Mystr;   
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "sub == " << sub << std::endl;   
    std::cout << std::endl;   
  
    std::cout << "sub < sub == " << std::boolalpha   
        << (sub < sub) << std::endl;   
  
    std::cout << "string(\"aab\") < sub == " << std::boolalpha   
        << (Mystr("aab") < sub) << std::endl;   
    std::cout << "sub < string(\"aab\") == " << std::boolalpha   
        << (sub < Mystr("aab")) << std::endl;   
  
    std::cout << "\"aab\" < sub == " << std::boolalpha   
        << ("aab" < sub) << std::endl;   
    std::cout << "sub < \"aab\" == " << std::boolalpha   
        << (sub < "aab") << std::endl;   
  
    std::cout << "'a' < sub == " << std::boolalpha   
        << ('a' < sub) << std::endl;   
    std::cout << "sub < 'a' == " << std::boolalpha   
        << (sub < 'a') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
sub == aaa  
  
sub < sub == false  
string("aab") < sub == false  
sub < string("aab") == true  
"aab" < sub == false  
sub < "aab" == true  
'a' < sub == true  
sub < 'a' == false  
```  
  
##  <a name="op_lt_lt"></a>operator&lt;&lt;  
 Wstawia sub_match — w strumieniu.  
  
```  
template <class Elem, class IOtraits, class Alloc, class BidIt>  
basic_ostream<Elem, IOtraits>& operator<<(basic_ostream<Elem, IOtraits>& os,  
    const sub_match<BidIt>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `Elem`  
 Typ elementu.  
  
 `IOtraits`  
 Klasa cech ciągu.  
  
 `Alloc`  
 Klasa alokatora.  
  
 `BidIt`  
 Typ iteratora.  
  
 `os`  
 Strumień danych wyjściowych.  
  
 `right`  
 Obiekt do wstawienia.  
  
### <a name="remarks"></a>Uwagi  
 Operator szablonu zwraca `os << right.str()`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__regex__operator_ins.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[0];   
    std::cout << "whole match: " << sub << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
whole match: caaa  
```  
  
##  <a name="op_lt_eq"></a>operator&lt;=  
 Mniejsze niż lub równa porównania dla różnych obiektów.  
  
```  
template <class BidIt>  
bool operator<=(const sub_match<BidIt>& left,  
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>  
bool operator<=(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,  
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>  
bool operator<=(const sub_match<BidIt>& left,  
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>  
bool operator<=(const typename iterator_traits<BidIt>::value_type *left,  
    const sub_match<BidIt>& right);

template <class BidIt>  
bool operator<=(const sub_match<BidIt>& left,  
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>  
bool operator<=(const typename iterator_traits<BidIt>::value_type& left,  
    const sub_match<BidIt>& right);

template <class BidIt>  
bool operator<=(const sub_match<BidIt>& left,  
    const typename iterator_traits<BidIt>::value_type& right);
```  
  
### <a name="parameters"></a>Parametry  
 `BidIt`  
 Typ iteratora.  
  
 `IOtraits`  
 Klasa cech ciągu.  
  
 `Alloc`  
 Klasa alokatora.  
  
 `left`  
 Po lewej stronie obiekt do porównania.  
  
 `right`  
 Prawy obiekt do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca każdego szablonu operatora `!(right < left)`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__regex__operator_le.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::cmatch::string_type Mystr;   
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "sub == " << sub << std::endl;   
    std::cout << std::endl;   
  
    std::cout << "sub <= sub == " << std::boolalpha   
        << (sub <= sub) << std::endl;   
  
    std::cout << "string(\"aab\") <= sub == " << std::boolalpha   
        << (Mystr("aab") <= sub) << std::endl;   
    std::cout << "sub <= string(\"aab\") == " << std::boolalpha   
        << (sub <= Mystr("aab")) << std::endl;   
  
    std::cout << "\"aab\" <= sub == " << std::boolalpha   
        << ("aab" <= sub) << std::endl;   
    std::cout << "sub <= \"aab\" == " << std::boolalpha   
        << (sub <= "aab") << std::endl;   
  
    std::cout << "'a' <= sub == " << std::boolalpha   
        << ('a' <= sub) << std::endl;   
    std::cout << "sub <= 'a' == " << std::boolalpha   
        << (sub <= 'a') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
sub == aaa  
  
sub <= sub == true  
string("aab") <= sub == false  
sub <= string("aab") == true  
"aab" <= sub == false  
sub <= "aab" == true  
'a' <= sub == true  
sub <= 'a' == false  
```  
  
##  <a name="op_eq_eq"></a>operator ==  
 Taki sam porównania dla różnych obiektów.  
  
```  
template <class BidIt>  
bool operator==(const sub_match<BidIt>& left,  
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>  
bool operator==(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,  
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>  
bool operator==(const sub_match<BidIt>& left,  
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>  
bool operator==(const typename iterator_traits<BidIt>::value_type* left,  
    const sub_match<BidIt>& right);

template <class BidIt>  
bool operator==(const sub_match<BidIt>& left,  
    const typename iterator_traits<BidIt>::value_type* right);

template <class BidIt>  
bool operator==(const typename iterator_traits<BidIt>::value_type& left,  
    const sub_match<BidIt>& right);

template <class BidIt>  
bool operator==(const sub_match<BidIt>& left,  
    const typename iterator_traits<BidIt>::value_type& right);

template <class BidIt, class Alloc>  
bool operator==(const match_results<BidIt, Alloc>& left,  
    const match_results<BidIt, Alloc>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `BidIt`  
 Typ iteratora.  
  
 `IOtraits`  
 Klasa cech ciągu.  
  
 `Alloc`  
 Klasa alokatora.  
  
 `left`  
 Po lewej stronie obiekt do porównania.  
  
 `right`  
 Prawy obiekt do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Operator każdego szablonu konwertuje każdego z jego argumentów typu ciąg i zwraca wynik porównanie przekonwertowanego obiektów pod kątem równości.  
  
 Gdy operator szablonu Konwertuje argumenty typu string używa pierwszy następujące przekształcenia, który ma zastosowanie:  
  
 argumenty, których typy są specjalizacji szablonu klasy `match_results` lub `sub_match` są konwertowane przez wywołanie metody `str` funkcja członkowska;  
  
 argumenty, których typy są specjalizacji szablonu klasy `basic_string` są takie same jak;  
  
 wszystkie inne typy argumentu są konwertowane przekazując wartość argumentu do konstruktora dla odpowiednich specjalizacji szablonu klasy `basic_string`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__regex__operator_eq.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::cmatch::string_type Mystr;   
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "match == " << mr.str() << std::endl;   
    std::cout << "sub == " << sub << std::endl;   
    std::cout << std::endl;   
  
    std::cout << "match == match == " << std::boolalpha   
        << (mr == mr) << std::endl;   
    std::cout << "sub == sub == " << std::boolalpha   
        << (sub == sub) << std::endl;   
  
    std::cout << "string(\"aab\") == sub == " << std::boolalpha   
        << (Mystr("aab") == sub) << std::endl;   
    std::cout << "sub == string(\"aab\") == " << std::boolalpha   
        << (sub == Mystr("aab")) << std::endl;   
  
    std::cout << "\"aab\" == sub == " << std::boolalpha   
        << ("aab" == sub) << std::endl;   
    std::cout << "sub == \"aab\" == " << std::boolalpha   
        << (sub == "aab") << std::endl;   
  
    std::cout << "'a' == sub == " << std::boolalpha   
        << ('a' == sub) << std::endl;   
    std::cout << "sub == 'a' == " << std::boolalpha   
        << (sub == 'a') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == caaa  
sub == aaa  
  
match == match == true  
sub == sub == true  
string("aab") == sub == false  
sub == string("aab") == false  
"aab" == sub == false  
sub == "aab" == false  
'a' == sub == false  
sub == 'a' == false  
```  
  
##  <a name="op_gt"></a>operator&gt;  
 Większa niż porównania dla różnych obiektów.  
  
```  
template <class BidIt>  
bool operator>(const sub_match<BidIt>& left,  
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>  
bool operator>(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,  
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>  
bool operator>(const sub_match<BidIt>& left,  
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>  
bool operator>(const typename iterator_traits<BidIt>::value_type *left,  
    const sub_match<BidIt>& right);

template <class BidIt>  
bool operator>(const sub_match<BidIt>& left,  
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>  
bool operator>(const typename iterator_traits<BidIt>::value_type& left,  
    const sub_match<BidIt>& right);

template <class BidIt>  
bool operator>(const sub_match<BidIt>& left,  
    const typename iterator_traits<BidIt>::value_type& right);
```  
  
### <a name="parameters"></a>Parametry  
 `BidIt`  
 Typ iteratora.  
  
 `IOtraits`  
 Klasa cech ciągu.  
  
 `Alloc`  
 Klasa alokatora.  
  
 `left`  
 Po lewej stronie obiekt do porównania.  
  
 `right`  
 Prawy obiekt do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca każdego szablonu operatora `right < left`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__regex__operator_gt.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::cmatch::string_type Mystr;   
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "sub == " << sub << std::endl;   
    std::cout << std::endl;   
  
    std::cout << "sub > sub == " << std::boolalpha   
        << (sub > sub) << std::endl;   
  
    std::cout << "string(\"aab\") > sub == " << std::boolalpha   
        << (Mystr("aab") > sub) << std::endl;   
    std::cout << "sub > string(\"aab\") == " << std::boolalpha   
        << (sub > Mystr("aab")) << std::endl;   
  
    std::cout << "\"aab\" > sub == " << std::boolalpha   
        << ("aab" > sub) << std::endl;   
    std::cout << "sub > \"aab\" == " << std::boolalpha   
        << (sub > "aab") << std::endl;   
  
    std::cout << "'a' > sub == " << std::boolalpha   
        << ('a' > sub) << std::endl;   
    std::cout << "sub > 'a' == " << std::boolalpha   
        << (sub > 'a') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
sub == aaa  
  
sub > sub == false  
string("aab") > sub == true  
sub > string("aab") == false  
"aab" > sub == true  
sub > "aab" == false  
'a' > sub == false  
sub > 'a' == true  
```  
  
##  <a name="op_gt_eq"></a>operator&gt;=  
 Większe lub równe porównania dla różnych obiektów.  
  
```  
template <class BidIt>  
bool operator>=(const sub_match<BidIt>& left,  
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>  
bool operator>=(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,  
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>  
bool operator>=(const sub_match<BidIt>& left,  
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>  
bool operator>=(const typename iterator_traits<BidIt>::value_type *left,  
    const sub_match<BidIt>& right);

template <class BidIt>  
bool operator>=(const sub_match<BidIt>& left,  
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>  
bool operator>=(const typename iterator_traits<BidIt>::value_type& left,  
    const sub_match<BidIt>& right);

template <class BidIt>  
bool operator>=(const sub_match<BidIt>& left,  
    const typename iterator_traits<BidIt>::value_type& right);
```  
  
### <a name="parameters"></a>Parametry  
 `BidIt`  
 Typ iteratora.  
  
 `IOtraits`  
 Klasa cech ciągu.  
  
 `Alloc`  
 Klasa alokatora.  
  
 `left`  
 Po lewej stronie obiekt do porównania.  
  
 `right`  
 Prawy obiekt do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca każdego szablonu operatora `!(left < right)`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__regex__operator_ge.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::cmatch::string_type Mystr;   
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "sub == " << sub << std::endl;   
    std::cout << std::endl;   
  
    std::cout << "sub >= sub == " << std::boolalpha   
        << (sub >= sub) << std::endl;   
  
    std::cout << "string(\"aab\") >= sub == " << std::boolalpha   
        << (Mystr("aab") >= sub) << std::endl;   
    std::cout << "sub >= string(\"aab\") == " << std::boolalpha   
        << (sub >= Mystr("aab")) << std::endl;   
  
    std::cout << "\"aab\" >= sub == " << std::boolalpha   
        << ("aab" >= sub) << std::endl;   
    std::cout << "sub >= \"aab\" == " << std::boolalpha   
        << (sub >= "aab") << std::endl;   
  
    std::cout << "'a' >= sub == " << std::boolalpha   
        << ('a' >= sub) << std::endl;   
    std::cout << "sub >= 'a' == " << std::boolalpha   
        << (sub >= 'a') << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
sub == aaa  
  
sub >= sub == true  
string("aab") >= sub == true  
sub >= string("aab") == false  
"aab" >= sub == true  
sub >= "aab" == false  
'a' >= sub == false  
sub >= 'a' == true  
```  
  
## <a name="see-also"></a>Zobacz też  
[\<wyrażenie regularne >](../standard-library/regex.md)  
[regex_constants — klasa](../standard-library/regex-constants-class.md)  
[regex_error — klasa](../standard-library/regex-error-class.md)  
[\<wyrażenie regularne > Funkcje](../standard-library/regex-functions.md)  
[regex_iterator — klasa](../standard-library/regex-iterator-class.md)  
[regex_token_iterator — klasa](../standard-library/regex-token-iterator-class.md)  
[regex_traits — klasa](../standard-library/regex-traits-class.md)  
[\<wyrażenie regularne > definicje typów](../standard-library/regex-typedefs.md)  



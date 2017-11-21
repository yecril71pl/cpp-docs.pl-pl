---
title: "&lt;ciąg&gt; operatory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- string/std::operator!=
- string/std::operator&gt;
- string/std::operator&gt;&gt;
- string/std::operator&gt;=
- string/std::operator&lt;
- string/std::operator&lt;&lt;
- string/std::operator&lt;=
- string/std::operator+
- string/std::operator==
dev_langs: C++
ms.assetid: 33ce8f05-06c7-45d3-a0cb-bcd27cf93910
caps.latest.revision: "11"
manager: ghogen
helpviewer_keywords:
- std::operator!= (string)
- std::operator&gt; (string)
- std::operator&gt;&gt; (string)
- std::operator&gt;= (string)
- std::operator&lt; (string)
- std::operator&lt;&lt; (string)
- std::operator&lt;= (string), std::operator== (string)
ms.openlocfilehash: caa6cad7f0801b5459bd2999ae38a3da52c00469
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltstringgt-operators"></a>&lt;ciąg&gt; operatory
||||  
|-|-|-|  
|[operator! =](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;&gt;](#op_gt_gt)|  
|[operator&gt;=](#op_gt_eq)|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|  
|[operator&lt;=](#op_lt_eq)|[operator +](#op_add)|[operator ==](#op_eq_eq)|  
  
##  <a name="op_add"></a>operator +  
 Łączy dwa obiekty ciągu.  
  
```  
template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,  
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,  
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,  
    const CharType right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator> operator+(
    const CharType* left,  
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator> operator+(
    const CharType left,  
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>& left,  
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,  
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,  
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,  
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,  
    CharType right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    const CharType* left,  
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    CharType left,  
    const basic_string<CharType, Traits, Allocator>&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` ma zostać połączony.  
  
 `right`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` ma zostać połączony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg, który jest złączeniem ciągów wejściowych.  
  
### <a name="remarks"></a>Uwagi  
 Przeciążenie funkcji każdego `operator+` do łączenia dwóch obiektów klasy szablonu [basic_string — klasa](../standard-library/basic-string-class.md). Wszystkie skutecznie zwracany `basic_string` \< **CharType**, **cech**, **alokatora**> (_ *lewej*). [Dołącz](../standard-library/basic-string-class.md#append)(\_ *prawej*).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// string_op_con.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   // Declaring an object of type basic_string<char>  
   string s1 ( "anti" );  
   string s2 ( "gravity" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "heroine";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // Declaring a character constant  
   char c1 = '!';  
   cout << "The character constant c1 = " << c1 << "." << endl;  
  
   // First member function: concatenates an  object  
   // of type basic_string with an object of type basic_string  
   string s12 = s1 + s2;  
   cout << "The string concatenating s1 & s2 is: " << s12 << endl;  
  
   // Second & fourth member functions: concatenate an object  
   // of type basic_string with an object of C-syle string type  
   string s1s3 = s1 + s3;  
   cout << "The string concatenating s1 & s3 is: " << s1s3 << endl;  
  
   // Third & fifth member functions: concatenate an object  
   // of type basic_string with a character constant  
   string s1s3c1 = s1s3 + c1;  
   cout << "The string concatenating s1 & s3 is: " << s1s3c1 << endl;  
}  
```  
  
```Output  
The basic_string s1 = anti.  
The basic_string s2 = gravity.  
The C-style string s3 = heroine.  
The character constant c1 = !.  
The string concatenating s1 & s2 is: antigravity  
The string concatenating s1 & s3 is: antiheroine  
The string concatenating s1 & s3 is: antiheroine!  
```  
  
##  <a name="op_neq"></a>operator! =  
 Testy, jeśli obiekt ciągu po lewej stronie operatora nie równa się z obiektem ciągu po prawej stronie.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left, 
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left, 
const CharType* right);

template <class CharType, class Traits, class Allocator>  
bool operator!=(
    const CharType* left, 
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` do porównania.  
  
 `right`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli nie jest obiektem ciągu po lewej stronie operatora lexicographically taki sam obiekt ciągu po prawej stronie, a w przeciwnym **false**.  
  
### <a name="remarks"></a>Uwagi  
 Porównanie obiektów string jest oparta na parowania lexicographical porównanie ich znaków. Dwa ciągi są takie same, jeśli mają taką samą liczbę znaków i ich wartości odpowiednich znaków są takie same. W przeciwnym razie ich nie są równe.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// string_op_ne.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "pluck" );  
   string s2 ( "strum" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "pluck";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // First member function: comparison between left-side object  
   // of type basic_string & right-side object of type basic_string  
   if ( s1 != s2 )  
      cout << "The strings s1 & s2 are not equal." << endl;  
   else  
      cout << "The strings s1 & s2 are equal." << endl;  
  
   // Second member function: comparison between left-side object  
   // of type basic_string & right-side object of C-syle string type  
   if ( s1 != s3 )  
      cout << "The strings s1 & s3 are not equal." << endl;  
   else  
      cout << "The strings s1 & s3 are equal." << endl;  
  
   // Third member function: comparison between left-side object  
   // of C-syle string type & right-side object of type basic_string  
   if ( s3 != s2 )  
      cout << "The strings s3 & s2 are not equal." << endl;  
   else  
      cout << "The strings s3 & s2 are equal." << endl;  
}  
```  
  
```Output  
The basic_string s1 = pluck.  
The basic_string s2 = strum.  
The C-style string s3 = pluck.  
The strings s1 & s2 are not equal.  
The strings s1 & s3 are equal.  
The strings s3 & s2 are not equal.  
```  
  
##  <a name="op_eq_eq"></a>operator ==  
 Testy, jeśli obiekt ciągu po lewej stronie operatora jest taki sam jak obiekt ciągu po prawej stronie.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left, 
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left, 
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
bool operator==(
    const CharType* left, 
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` do porównania.  
  
 `right`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli obiekt ciągu po lewej stronie operatora jest lexicographically taki sam obiekt ciągu po prawej stronie; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Porównanie obiektów string jest oparta na parowania lexicographical porównanie ich znaków. Dwa ciągi są takie same, jeśli mają taką samą liczbę znaków i ich wartości odpowiednich znaków są takie same. W przeciwnym razie ich nie są równe.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// string_op_eq.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "pluck" );  
   string s2 ( "strum" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "pluck";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // First member function: comparison between left-side object  
   // of type basic_string & right-side object of type basic_string  
   if ( s1 == s2 )  
      cout << "The strings s1 & s2 are equal." << endl;  
   else  
      cout << "The strings s1 & s2 are not equal." << endl;  
  
   // Second member function: comparison between left-side object  
   // of type basic_string & right-side object of C-syle string type  
   if ( s1 == s3 )  
      cout << "The strings s1 & s3 are equal." << endl;  
   else  
      cout << "The strings s1 & s3 are not equal." << endl;  
  
   // Third member function: comparison between left-side object  
   // of C-syle string type & right-side object of type basic_string  
   if ( s3 == s2 )  
      cout << "The strings s3 & s2 are equal." << endl;  
   else  
      cout << "The strings s3 & s2 are not equal." << endl;  
}  
```  
  
```Output  
The basic_string s1 = pluck.  
The basic_string s2 = strum.  
The C-style string s3 = pluck.  
The strings s1 & s2 are not equal.  
The strings s1 & s3 are equal.  
The strings s3 & s2 are not equal.  
```  
  
##  <a name="op_lt"></a>operator&lt;  
 Sprawdza, czy z obiektem ciągu po lewej stronie operatora jest mniejsza niż z obiektem ciągu po prawej stronie.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left, 
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left, 
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
bool operator<(
    const CharType* left, 
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` do porównania.  
  
 `right`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** w przypadku z obiektem ciągu po lewej stronie operatora lexicographically mniej niż obiekt ciągu po prawej stronie; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Lexicographical porównania ciągów porównuje je znak po znaku do:  
  
-   Znajdzie odpowiedniego znakami nierówne i pochodzi wynik ich porównanie wyniku porównania ciągów.  
  
-   Znalezione nie nierówności, ale jeden ciąg ma więcej znaków niż innych i krótszego ciągu jest uważany za mniej niż ciąg dłużej.  
  
-   Znalezione nie nierówności i wyszukuje czy ciągi mają taką samą liczbę znaków, a więc ciągi są takie same.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// string_op_lt.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "strict" );  
   string s2 ( "strum" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "strict";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // First member function: comparison between left-side object  
   // of type basic_string & right-side object of type basic_string  
   if ( s1 < s2 )  
      cout << "The string s1 is less than the string s2." << endl;  
   else  
      cout << "The string s1 is not less than the string s2." << endl;  
  
   // Second member function: comparison between left-hand object  
   // of type basic_string & right-hand object of C-syle string type  
   if ( s1 < s3 )  
      cout << "The string s1 is less than the string s3." << endl;  
   else  
      cout << "The string s1 is not less than the string s3." << endl;  
  
   // Third member function: comparison between left-hand object  
   // of C-syle string type & right-hand object of type basic_string  
   if ( s3 < s2 )  
      cout << "The string s3 is less than the string s2." << endl;  
   else  
      cout << "The string s3 is not less than the string s2." << endl;  
}  
```  
  
```Output  
The basic_string s1 = strict.  
The basic_string s2 = strum.  
The C-style string s3 = strict.  
The string s1 is less than the string s2.  
The string s1 is not less than the string s3.  
The string s3 is less than the string s2.  
```  
  
##  <a name="op_lt_eq"></a>operator&lt;=  
 Testy, jeśli ciąg obiekt po lewej stronie operatora jest mniejsza niż lub równe z obiektem ciągu po prawej stronie.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left, 
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left, 
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
bool operator<=(
    const CharType* left, 
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` do porównania.  
  
 `right`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** w przypadku z obiektem ciągu po lewej stronie operatora lexicographically mniejsze niż lub równe z obiektem ciągu po prawej stronie, w przeciwnym **false**.  
  
### <a name="remarks"></a>Uwagi  
 Lexicographical porównania ciągów porównuje je znak po znaku do:  
  
-   Znajdzie odpowiedniego znakami nierówne i pochodzi wynik ich porównanie wyniku porównania ciągów.  
  
-   Znalezione nie nierówności, ale jeden ciąg ma więcej znaków niż innych i krótszego ciągu jest uważany za mniej niż ciąg dłużej.  
  
-   Znalezione nie nierówności i stwierdzi, że ciągi mają taką samą liczbę znaków, dlatego ciągi są takie same.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// string_op_le.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "strict" );  
   string s2 ( "strum" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "strict";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // First member function: comparison between left-side object  
   // of type basic_string & right-side object of type basic_string  
   if ( s1 <= s2 )  
      cout << "The string s1 is less than or equal to "  
           << "the string s2." << endl;  
   else  
      cout << "The string s1 is greater than "  
           << "the string s2." << endl;  
  
   // Second member function: comparison between left-side object  
   // of type basic_string & right-side object of C-syle string type  
   if ( s1 <= s3 )  
      cout << "The string s1 is less than or equal to "  
           << "the string s3." << endl;  
   else  
      cout << "The string s1 is greater than "  
           << "the string s3." << endl;  
  
   // Third member function: comparison between left-side object  
   // of C-syle string type  & right-side object of type basic_string  
   if ( s2 <= s3 )  
      cout << "The string s2 is less than or equal to "  
           << "the string s3." << endl;  
   else  
      cout << "The string s2 is greater than "  
           << "the string s3." << endl;  
}  
```  
  
```Output  
The basic_string s1 = strict.  
The basic_string s2 = strum.  
The C-style string s3 = strict.  
The string s1 is less than or equal to the string s2.  
The string s1 is less than or equal to the string s3.  
The string s2 is greater than the string s3.  
```  
  
##  <a name="op_lt_lt"></a>operator&lt;&lt;  
 Funkcja szablonu, która zapisuje ciąg do strumienia wyjściowego.  
  
```  
template <class CharType, class Traits, class Allocator>  
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& _Ostr, 
    const basic_string<CharType, Traits, Allocator>& str);
```  
  
### <a name="parameters"></a>Parametry  
 _Ostr  
 Zapisywane do strumienia wyjściowego.  
  
 `str`  
 Ciąg, który można wprowadzić do strumienia wyjściowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zapisuje wartość ciągu określona do strumienia wyjściowego `_Ostr`.  
  
### <a name="remarks"></a>Uwagi  
 Przeciążenia funkcji szablonu **operator <<** do wstawienia _ obiektu *Str* szablonu klasy [basic_string —](../standard-library/basic-string-class.md) do strumienia \_  *OSTR.* Funkcja skutecznie zwraca \_ *Ostr*. **zapis**( \_ *Str*. [c_str](../standard-library/basic-string-class.md#c_str), \_ *Str*. [rozmiar](../standard-library/basic-string-class.md#size)).  
  
##  <a name="op_gt"></a>operator&gt;  
 Testy, jeśli obiekt ciągu po lewej stronie operatora jest większa niż z obiektem ciągu po prawej stronie.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left, 
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left, 
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
bool operator>(
    const CharType* left, 
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` do porównania.  
  
 `right`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli obiekt ciągu po lewej stronie operatora jest lexicographically większy niż obiekt ciągu po prawej stronie; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Lexicographical porównania ciągów porównuje je znak po znaku do:  
  
-   Znajdzie odpowiedniego znakami nierówne i pochodzi wynik ich porównanie wyniku porównania ciągów.  
  
-   Znalezione nie nierówności, ale jeden ciąg ma więcej znaków niż innych i krótszego ciągu jest uważany za mniej niż ciąg dłużej.  
  
-   Znalezione nie nierówności i wyszukuje czy ciągi mają taką samą liczbę znaków, a więc ciągi są takie same.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// string_op_gt.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "strict" );  
   string s2 ( "strum" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "stricture";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // First member function: comparison between left-side object  
   // of type basic_string & right-side object of type basic_string  
   if ( s1 > s2 )  
      cout << "The string s1 is greater than "  
           << "the string s2." << endl;  
   else  
      cout << "The string s1 is not greater than "  
           << "the string s2." << endl;  
  
   // Second member function: comparison between left-side object  
   // of type basic_string & right-side object of C-syle string type  
   if ( s3 > s1 )  
      cout << "The string s3 is greater than "  
           << "the string s1." << endl;  
   else  
      cout << "The string s3 is not greater than "  
           << "the string s1." << endl;  
  
   // Third member function: comparison between left-side object  
   // of C-syle string type & right-side object of type basic_string  
   if ( s2 > s3 )  
      cout << "The string s2 is greater than "  
           << "the string s3." << endl;  
   else  
      cout << "The string s2 is not greater than "  
           << "the string s3." << endl;  
}  
```  
  
```Output  
The basic_string s1 = strict.  
The basic_string s2 = strum.  
The C-style string s3 = stricture.  
The string s1 is not greater than the string s2.  
The string s3 is greater than the string s1.  
The string s2 is greater than the string s3.  
```  
  
##  <a name="op_gt_eq"></a>operator&gt;=  
 Testy, jeśli obiekt ciągu po lewej stronie operatora jest większa niż lub równa z obiektem ciągu po prawej stronie.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left, 
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left, 
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
bool operator>=(
    const CharType* left, 
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` do porównania.  
  
 `right`  
 Ciąg w stylu języka C lub typu obiektu `basic_string` do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli obiekt ciągu po lewej stronie operatora jest lexicographically większa niż lub równa z obiektem ciągu po prawej stronie, a w przeciwnym **false**.  
  
### <a name="remarks"></a>Uwagi  
 Lexicographical porównania ciągów porównuje je znak po znaku do:  
  
-   Znajdzie odpowiedniego znakami nierówne i pochodzi wynik ich porównanie wyniku porównania ciągów.  
  
-   Znalezione nie nierówności, ale jeden ciąg ma więcej znaków niż innych i krótszego ciągu jest uważany za mniej niż ciąg dłużej.  
  
-   Znalezione nie nierówności i wyszukuje ciągi mają taką samą liczbę znaków, a więc ciągi są takie same.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// string_op_ge.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "strict" );  
   string s2 ( "strum" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "stricture";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // First member function: comparison between left-side object  
   // of type basic_string & right-side object of type basic_string  
   if ( s1 >= s2 )  
      cout << "The string s1 is greater than or equal to "  
           << "the string s2." << endl;  
   else  
      cout << "The string s1 is less than "  
           << "the string s2." << endl;  
  
   // Second member function: comparison between left-side object  
   // of type basic_string & right-side object of C-syle string type  
   if ( s3 >= s1 )  
      cout << "The string s3 is greater than or equal to "  
           << "the string s1." << endl;  
   else  
      cout << "The string s3 is less than "  
           << "the string s1." << endl;  
  
   // Third member function: comparison between left-side object  
   // of C-syle string type & right-side object of type basic_string  
   if ( s2 >= s3 )  
      cout << "The string s2 is greater than or equal to "  
           << "the string s3." << endl;  
   else  
      cout << "The string s2 is less than "  
           << "the string s3." << endl;  
}  
```  
  
```Output  
The basic_string s1 = strict.  
The basic_string s2 = strum.  
The C-style string s3 = stricture.  
The string s1 is less than the string s2.  
The string s3 is greater than or equal to the string s1.  
The string s2 is greater than or equal to the string s3.  
```  
  
##  <a name="op_gt_gt"></a>operator&gt;&gt;  
 Funkcja szablonu, która odczytuje ciąg ze strumienia wejściowego.  
  
```  
template <class CharType, class Traits, class Allocator>  
basic_istream<CharType, Traits>& operator>>(
    basic_istream<CharType, Traits>& _Istr,  
    basic_string<CharType, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `_Istr`  
 Strumień wejściowy używany do wyodrębnienia sekwencji  
  
 `right`  
 Ciąg, który jest wyodrębniania ze strumienia wejściowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odczytuje wartości z określonego ciągu `_Istr` i zwraca go do `right`.  
  
### <a name="remarks"></a>Uwagi  
 Operator pomija spacje początkowe białe, chyba że `skipws` flaga jest ustawiona. Odczytuje wszystkie następujące znaki do momentu następnej znak spacji lub zostanie osiągnięty koniec pliku.  
  
 Przeciążenia funkcji szablonu **operator >>** zastąpić sekwencji kontrolowane przez `right` z sekwencją elementów wyodrębnione ze strumienia `_Istr`. Zatrzymuje wyodrębniania:  
  
-   Na końcu pliku.  
  
-   Po wyodrębnia funkcji `_Istr`. **szerokość** elementy, jeśli ta wartość jest różna od zera.  
  
 Po wyodrębnia funkcji `_Istr`. [max_size](../standard-library/basic-string-class.md#max_size) elementów.  
  
-   Po funkcji wyodrębnia element *ch* dla którego [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **CharType**> > ( `getloc`). **jest**( **ctype** \< **CharType**>:: **miejsca**, *ch*) ma wartość true, w którym to przypadku znak jest umieszczany Wstecz.  
  
 Jeśli funkcja wyodrębnia żadnych elementów, wywołuje metodę [metoda setstate](../standard-library/basic-ios-class.md#setstate)( `ios_base::failbit`). W każdym przypadku wywołuje **istr**. **szerokość**(0) i zwraca \* **to**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// string_op_read_.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   string c0;  
   cout << "Input a string c0 ( try: Fibonacci numbers ): ";  
   cin >> c0;  
   cout << "The string entered is c0 = " << c0 << endl;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<ciąg >](../standard-library/string.md)

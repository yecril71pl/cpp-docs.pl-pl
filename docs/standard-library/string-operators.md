---
title: '&lt;Operatory&gt; ciągów'
ms.date: 11/04/2016
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
ms.assetid: 33ce8f05-06c7-45d3-a0cb-bcd27cf93910
helpviewer_keywords:
- std::operator!= (string)
- std::operator&gt; (string)
- std::operator&gt;&gt; (string)
- std::operator&gt;= (string)
- std::operator&lt; (string)
- std::operator&lt;&lt; (string)
- std::operator&lt;= (string), std::operator== (string)
ms.openlocfilehash: bb66e7c0120da9f140ce33da7ecc61299a4d2867
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459258"
---
# <a name="ltstringgt-operators"></a>&lt;Operatory&gt; ciągów

||||
|-|-|-|
|[operator!=](#op_neq)|[zakład&gt;](#op_gt)|[zakład&gt;&gt;](#op_gt_gt)|
|[zakład&gt;=](#op_gt_eq)|[zakład&lt;](#op_lt)|[zakład&lt;&lt;](#op_lt_lt)|
|[zakład&lt;=](#op_lt_eq)|[operator +](#op_add)|[operator==](#op_eq_eq)|

## <a name="op_add"></a>operator +

Łączy dwa obiekty String.

```cpp
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

*lewym*\
Ciąg w stylu C lub obiekt typu `basic_string` do łączenia.

*Kliknij*\
Ciąg w stylu C lub obiekt typu `basic_string` do łączenia.

### <a name="return-value"></a>Wartość zwracana

Ciąg, który jest połączeniem ciągów wejściowych.

### <a name="remarks"></a>Uwagi

Funkcja każdego przeciążenia `operator+` do łączenia dwóch obiektów klasy szablonu Klasa [basic_string](../standard-library/basic-string-class.md). Wszystkie skutecznie zwracają `basic_string< CharType, Traits, Allocator>(Left).append(right)`. Aby uzyskać więcej informacji, [](../standard-library/basic-string-class.md#append)zobacz Dołączanie.

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

## <a name="op_neq"></a>operator! =

Testuje, czy obiekt String po lewej stronie operatora nie jest równy obiektowi ciągu po prawej stronie.

```cpp
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

*lewym*\
Ciąg w stylu C lub obiekt typu `basic_string` , który ma zostać porównany.

*Kliknij*\
Ciąg w stylu C lub obiekt typu `basic_string` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli obiekt String po lewej stronie operatora nie jest lexicographically równy obiektowi ciągu po prawej stronie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów String jest oparte na przełożeniu lexicographical, porównując ich znaki. Dwa ciągi są równe, jeśli mają taką samą liczbę znaków, a ich odpowiednie wartości znakowe są takie same. W przeciwnym razie są one nierówne.

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

## <a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt String po lewej stronie operatora jest równy obiektowi ciągu po prawej stronie.

```cpp
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

*lewym*\
Ciąg w stylu C lub obiekt typu `basic_string` , który ma zostać porównany.

*Kliknij*\
Ciąg w stylu C lub obiekt typu `basic_string` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

**true** , jeśli obiekt String po lewej stronie operatora jest lexicographically równy obiektowi ciągu po prawej stronie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie obiektów String jest oparte na przełożeniu lexicographical, porównując ich znaki. Dwa ciągi są równe, jeśli mają taką samą liczbę znaków, a ich odpowiednie wartości znakowe są takie same. W przeciwnym razie są one nierówne.

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

## <a name="op_lt"></a>zakład&lt;

Testuje, czy obiekt String po lewej stronie operatora jest mniejszy niż obiekt ciągu po prawej stronie.

```cpp
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

*lewym*\
Ciąg w stylu C lub obiekt typu `basic_string` , który ma zostać porównany.

*Kliknij*\
Ciąg w stylu C lub obiekt typu `basic_string` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

**true** , jeśli obiekt String po lewej stronie operatora jest lexicographically mniejszy niż obiekt String po prawej stronie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między ciągami porównuje znak według znaku do momentu:

- Znajduje dwa odpowiednie znaki nierówne, a wynik porównania jest traktowany jako wynik porównania między ciągami.

- Nie ma żadnej nierówności, ale jeden ciąg ma więcej znaków niż drugi, a krótszy ciąg jest uznawany za krótszy niż dłuższy ciąg.

- Nie ma żadnej nierówności i stwierdza, że ciągi mają taką samą liczbę znaków, dlatego ciągi są równe.

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

## <a name="op_lt_eq"></a>zakład&lt;=

Testuje, czy obiekt String po lewej stronie operatora jest mniejszy niż lub równy obiektowi ciągu po prawej stronie.

```cpp
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

*lewym*\
Ciąg w stylu C lub obiekt typu `basic_string` , który ma zostać porównany.

*Kliknij*\
Ciąg w stylu C lub obiekt typu `basic_string` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

**true** , jeśli obiekt String po lewej stronie operatora jest lexicographically mniejszy lub równy obiektowi ciągu po prawej stronie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między ciągami porównuje znak według znaku do momentu:

- Znajduje dwa odpowiednie znaki nierówne, a wynik porównania jest traktowany jako wynik porównania między ciągami.

- Nie ma żadnej nierówności, ale jeden ciąg ma więcej znaków niż drugi, a krótszy ciąg jest uznawany za krótszy niż dłuższy ciąg.

- Nie ma żadnej nierówności i stwierdza, że ciągi mają taką samą liczbę znaków, więc ciągi są równe.

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

## <a name="op_lt_lt"></a>zakład&lt;&lt;

Funkcja szablonu, która zapisuje ciąg w strumieniu wyjściowym.

```cpp
template <class CharType, class Traits, class Allocator>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& _Ostr,
    const basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parametry

*_Ostr*\
Docelowy strumień danych wyjściowych.

*str*\
Ciąg, który ma zostać wprowadzony do strumienia wyjściowego.

### <a name="return-value"></a>Wartość zwracana

Zapisuje wartość określonego ciągu do strumienia wyjściowego *_Ostr*.

### <a name="remarks"></a>Uwagi

Operator przeciążania funkcji szablonu **< <** , aby wstawić obiekt *str* klasy szablonu [basic_string](../standard-library/basic-string-class.md) do  *\_ostr*strumienia. Funkcja efektywnie zwraca wartość `_Ostr.write( str.c_str, str.size )`.

## <a name="op_gt"></a>zakład&gt;

Testuje, czy obiekt String po lewej stronie operatora jest większy niż obiekt ciągu po prawej stronie.

```cpp
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

*lewym*\
Ciąg w stylu C lub obiekt typu `basic_string` , który ma zostać porównany.

*Kliknij*\
Ciąg w stylu C lub obiekt typu `basic_string` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

**true** , jeśli obiekt String po lewej stronie operatora jest lexicographically większy niż obiekt String po prawej stronie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między ciągami porównuje znak według znaku do momentu:

- Znajduje dwa odpowiednie znaki nierówne, a wynik porównania jest traktowany jako wynik porównania między ciągami.

- Nie ma żadnej nierówności, ale jeden ciąg ma więcej znaków niż drugi, a krótszy ciąg jest uznawany za krótszy niż dłuższy ciąg.

- Nie ma żadnej nierówności i stwierdza, że ciągi mają taką samą liczbę znaków, dlatego ciągi są równe.

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

## <a name="op_gt_eq"></a>zakład&gt;=

Testuje, czy obiekt String po lewej stronie operatora jest większy niż lub równy obiektowi ciągu po prawej stronie.

```cpp
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

*lewym*\
Ciąg w stylu C lub obiekt typu `basic_string` , który ma zostać porównany.

*Kliknij*\
Ciąg w stylu C lub obiekt typu `basic_string` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

**true** , jeśli obiekt String po lewej stronie operatora jest lexicographically większy lub równy obiektowi ciągu po prawej stronie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między ciągami porównuje znak według znaku do momentu:

- Znajduje dwa odpowiednie znaki nierówne, a wynik porównania jest traktowany jako wynik porównania między ciągami.

- Nie ma żadnej nierówności, ale jeden ciąg ma więcej znaków niż drugi, a krótszy ciąg jest uznawany za krótszy niż dłuższy ciąg.

- Nie ma żadnej nierówności i znajduje ciągi mają taką samą liczbę znaków, dlatego ciągi są równe.

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

## <a name="op_gt_gt"></a>zakład&gt;&gt;

Funkcja szablonu, która odczytuje ciąg ze strumienia wejściowego.

```cpp
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& operator>>(
    basic_istream<CharType, Traits>& _Istr,
    basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*_Istr*\
Strumień wejściowy używany do wyodrębniania sekwencji

*Kliknij*\
Ciąg, który jest wyodrębniany ze strumienia wejściowego.

### <a name="return-value"></a>Wartość zwracana

Odczytuje wartość określonego ciągu z *_Istr* i zwraca go do *prawej*.

### <a name="remarks"></a>Uwagi

Operator pomija wiodące białe znaki, chyba że `skipws` flaga jest ustawiona. Odczytuje wszystkie następujące znaki do momentu, aż następny znak jest odstępem lub zostanie osiągnięty koniec pliku.

Operator przeciążania funkcji szablonu **> >** do zastępowania sekwencji kontrolowanej przez *prawo* z sekwencją elementów wyodrębnionych ze strumienia *_Istr*. Ekstrakcja zostaje zatrzymana:

- Na końcu pliku.

- Po wyodrębnieniu `_Istr`funkcji. **Width** , jeśli ta wartość jest różna od zera.

Po wyodrębnieniu `_Istr`funkcji. elementy [max_size](../standard-library/basic-string-class.md#max_size) .

- Po wyodrębnieniu przez funkcję elementu *ch* , dla którego [use_facet](../standard-library/basic-filebuf-class.md#open)< **CType** \< **CharType**> > `getloc`(). **jest** ( **CType** \< **CharType**>:: **Space**, *ch*) ma wartość true, a w takim przypadku znak jest umieszczany ponownie.

Jeśli funkcja nie wyodrębni żadnych elementów, wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(`ios_base::failbit`). W każdym przypadku wywołuje **ISTR**. **Szerokość** (0) i zwraca \* **tę**wartość.

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

## <a name="see-also"></a>Zobacz także

[\<ciąg >](../standard-library/string.md)

---
title: '&lt;&gt;funkcje regionalne'
ms.date: 11/04/2016
f1_keywords:
- locale/std::has_facet
- locale/std::isalnum
- locale/std::isalpha
- locale/std::iscntrl
- locale/std::isdigit
- locale/std::isgraph
- locale/std::islower
- locale/std::isprint
- locale/std::ispunct
- locale/std::isspace
- locale/std::isupper
- locale/std::isxdigit
- locale/std::tolower
- locale/std::toupper
- locale/std::use_facet
ms.assetid: b06c1ceb-33a7-48d3-8d4b-2714bbb27f14
helpviewer_keywords:
- std::has_facet [C++]
- std::isalnum [C++]
- std::isalpha [C++]
- std::iscntrl [C++]
- std::isdigit [C++]
- std::isgraph [C++]
- std::islower [C++]
- std::isprint [C++]
- std::ispunct [C++]
- std::isspace [C++]
- std::isupper [C++]
- std::isxdigit [C++]
- std::tolower [C++]
- std::toupper [C++]
- std::use_facet [C++]
ms.openlocfilehash: 91d0b40de557eb2414d6ee685795796c3290177c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833247"
---
# <a name="ltlocalegt-functions"></a>&lt;&gt;funkcje regionalne

[has_facet](#has_facet)\
[isalnum](#isalnum)\
[isalpha](#isalpha)\
[iscntrl](#iscntrl)\
[IsDigit](#isdigit)\
[isgraf](#isgraph)\
[IsLower](#islower)\
[isprint](#isprint)\
[ispunct](#ispunct)\
[isspace](#isspace)\
[IsUpper](#isupper)\
[isxdigit](#isxdigit)\
[ToLower](#tolower)\
[ToUpper](#toupper)\
[use_facet](#use_facet)

## <a name="has_facet"></a><a name="has_facet"></a> has_facet

Sprawdza, czy określony zestaw reguł jest przechowywany w określonych ustawieniach regionalnych.

```cpp
template <class Facet>
bool has_facet(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Ustawienia regionalne, które mają być testowane dla obecności zestawu reguł.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli ustawienia regionalne mają zestaw reguł testowany dla; **`false`** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest przydatna do sprawdzania, czy zestawy nieobowiązkowe są wymienione w ustawieniach regionalnych przed `use_facet` wywołaniem, aby uniknąć wyjątku, który będzie zgłaszany, jeśli nie był obecny.

### <a name="example"></a>Przykład

```cpp
// locale_has_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result = has_facet <ctype<char> > ( loc );
   cout << result << endl;
}
```

```Output
1
```

## <a name="isalnum"></a><a name="isalnum"></a> isalnum

Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfabetycznym czy liczbowym.

```cpp
template <class CharType>
bool isalnum(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Element alfanumeryczny do przetestowania.

*Loc*\
Ustawienia regionalne zawierające element alfanumeryczny do przetestowania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli testowany element jest alfanumeryczny; **`false`** Jeśli tak nie jest.

### <a name="example"></a>Przykład

```cpp
// locale_isalnum.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalnum ( 'L', loc);
   bool result2 = isalnum ( '@', loc);
   bool result3 = isalnum ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphanumeric." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphanumeric." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphanumeric." << endl;
}
```

```Output
The character 'L' in the locale is alphanumeric.
The character '@' in the locale is  not alphanumeric.
The character '3' in the locale is alphanumeric.
```

## <a name="isalpha"></a><a name="isalpha"></a> isalpha

Testuje, czy element w ustawieniach regionalnych jest znakiem alfabetycznym.

```cpp
template <class CharType>
bool isalpha(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do przetestowania.

*Loc*\
Ustawienia regionalne zawierające element alfabetyczny do przetestowania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli testowany element jest alfabetyczny; **`false`** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [is](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Alpha**, `Ch` ).

### <a name="example"></a>Przykład

```cpp
// locale_isalpha.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalpha ( 'L', loc);
   bool result2 = isalpha ( '@', loc);
   bool result3 = isalpha ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphabetic." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphabetic." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphabetic." << endl;
}
```

## <a name="iscntrl"></a><a name="iscntrl"></a> iscntrl

Sprawdza, czy element w ustawieniach regionalnych jest znakiem kontrolnym.

```cpp
template <class CharType>
bool iscntrl(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do przetestowania.

*Loc*\
Ustawienia regionalne zawierające element do przetestowania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli testowany element jest znakiem kontrolnym; **`false`** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [is](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **cntrl**, `Ch` ).

### <a name="example"></a>Przykład

```cpp
// locale_iscntrl.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = iscntrl ( 'L', loc );
   bool result2 = iscntrl ( '\n', loc );
   bool result3 = iscntrl ( '\t', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a control character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a control character." << endl;

   if ( result2 )
      cout << "The character-set 'backslash-n' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale\n is "
           << " not a control character." << endl;

   if ( result3 )
      cout << "The character-set 'backslash-t' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale \n is "
           << " not a control character." << endl;
}
```

## <a name="isdigit"></a><a name="isdigit"></a> IsDigit

Sprawdza, czy element w ustawieniach regionalnych jest znakiem liczbowym.

```cpp
template <class CharType>
bool isdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do przetestowania.

*Loc*\
Ustawienia regionalne zawierające element do przetestowania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli testowany element jest znakiem numerycznym; **`false`** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [is](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **cyfra** `Ch` ).

### <a name="example"></a>Przykład

```cpp
// locale_is_digit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isdigit ( 'L', loc );
   bool result2 = isdigit ( '@', loc );
   bool result3 = isdigit ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a numeric character." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not a numeric character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a numeric character." << endl;
}
```

## <a name="isgraph"></a><a name="isgraph"></a> isgraf

Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfanumerycznym lub interpunkcyjnym.

```cpp
template <class CharType>
bool isgraph(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do przetestowania.

*Loc*\
Ustawienia regionalne zawierające element do przetestowania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli testowany element jest znakiem alfanumerycznym lub interpunkcją; **`false`** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [is](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Graph**, `Ch` ).

### <a name="example"></a>Przykład

```cpp
// locale_is_graph.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isgraph ( 'L', loc );
   bool result2 = isgraph ( '\t', loc );
   bool result3 = isgraph ( '.', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;

   if ( result2 )
      cout << "The character 'backslash-t' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is\n "
           << "not an alphanumeric or punctuation character." << endl;

   if ( result3 )
      cout << "The character '.' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character '.' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;
}
```

## <a name="islower"></a><a name="islower"></a> IsLower

Sprawdza, czy element w ustawieniach regionalnych jest pisany małymi literami.

```cpp
template <class CharType>
bool islower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do przetestowania.

*Loc*\
Ustawienia regionalne zawierające element do przetestowania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli testowany element jest małą literą; **`false`** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [is](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Lower**, `Ch` ).

### <a name="example"></a>Przykład

```cpp
// locale_islower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = islower ( 'L', loc );
   bool result2 = islower ( 'n', loc );
   bool result3 = islower ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a lowercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a lowercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a lowercase character." << endl;
}
```

## <a name="isprint"></a><a name="isprint"></a> isprint

Sprawdza, czy element w ustawieniach regionalnych jest znakiem drukowalnym.

```cpp
template <class CharType>
bool isprint(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do przetestowania.

*Loc*\
Ustawienia regionalne zawierające element do przetestowania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli testowany element jest drukowalny; **`false`** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [is](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Print**, `Ch` ).

### <a name="example"></a>Przykład

```cpp
// locale_isprint.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );

   bool result1 = isprint ( 'L', loc );
   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a printable character." << endl;

   bool result2 = isprint( '\t', loc );
   if ( result2 )
      cout << "The character 'backslash-t' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is "
           << " not a printable character." << endl;

   bool result3 = isprint( '\n', loc );
   if ( result3 )
      cout << "The character 'backslash-n' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a printable character." << endl;
}
```

## <a name="ispunct"></a><a name="ispunct"></a> ispunct

Sprawdza, czy element w ustawieniach regionalnych jest znakiem interpunkcyjnym.

```cpp
template <class CharType>
bool ispunct(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do przetestowania.

*Loc*\
Ustawienia regionalne zawierające element do przetestowania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli testowany element jest znakiem interpunkcji; **`false`** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [use_facet](../standard-library/locale-functions.md#use_facet) `<` [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [is](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **punct**, `Ch` ).

### <a name="example"></a>Przykład

```cpp
// locale_ispunct.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = ispunct ( 'L', loc );
   bool result2 = ispunct ( ';', loc );
   bool result3 = ispunct ( '*', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a punctuation character." << endl;

   if ( result2 )
      cout << "The character ';' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character ';' in the locale is "
           << " not a punctuation character." << endl;

   if ( result3 )
      cout << "The character '*' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character '*' in the locale is "
           << " not a punctuation character." << endl;
}
```

## <a name="isspace"></a><a name="isspace"></a> isspace

Sprawdza, czy element w ustawieniach regionalnych jest znakiem białym.

```cpp
template <class CharType>
bool isspace(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do przetestowania.

*Loc*\
Ustawienia regionalne zawierające element do przetestowania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli testowany element jest znakiem odstępu; **`false`** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [is](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Space**, `Ch` ).

### <a name="example"></a>Przykład

```cpp
// locale_isspace.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isspace ( 'L', loc );
   bool result2 = isspace ( '\n', loc );
   bool result3 = isspace ( ' ', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a whitespace character." << endl;

   if ( result2 )
      cout << "The character 'backslash-n' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a whitespace character." << endl;

   if ( result3 )
      cout << "The character ' ' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character ' ' in the locale is "
           << " not a whitespace character." << endl;
}
```

## <a name="isupper"></a><a name="isupper"></a> IsUpper

Testuje, czy element w ustawieniach regionalnych jest wielką literą.

```cpp
template <class CharType>
bool isupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do przetestowania.

*Loc*\
Ustawienia regionalne zawierające element do przetestowania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli testowany element jest znakiem wielką literą; **`false`** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [is](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Upper**, `Ch` ).

### <a name="example"></a>Przykład

```cpp
// locale_isupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isupper ( 'L', loc );
   bool result2 = isupper ( 'n', loc );
   bool result3 = isupper ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a uppercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a uppercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a uppercase character." << endl;
}
```

## <a name="isxdigit"></a><a name="isxdigit"></a> isxdigit

Sprawdza, czy element w ustawieniach regionalnych jest znakiem używanym do reprezentowania liczby w postaci szesnastkowej.

```cpp
template <class CharType>
bool isxdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do przetestowania.

*Loc*\
Ustawienia regionalne zawierające element do przetestowania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli testowany element jest znakiem używanym do reprezentowania liczby szesnastkowej; **`false`** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [is](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **xdigit**, `Ch` ).

Cyfry szesnastkowe wykorzystują 16, aby reprezentować liczby, używając cyfr od 0 do 9 oraz liter bez uwzględniania wielkości liter od do F, aby reprezentować liczby dziesiętne od 0 do 15.

### <a name="example"></a>Przykład

```cpp
// locale_isxdigit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isxdigit ( '5', loc );
   bool result2 = isxdigit ( 'd', loc );
   bool result3 = isxdigit ( 'q', loc );

   if ( result1 )
      cout << "The character '5' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character '5' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result2 )
      cout << "The character 'd' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'd' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result3 )
      cout << "The character 'q' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'q' in the locale is "
           << " not a hexidecimal digit-character." << endl;
}
```

## <a name="tolower"></a><a name="tolower"></a> ToLower

Konwertuje znak do małej litery.

```cpp
template <class CharType>
CharType tolower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak do przekonwertowania na małe litery.

*Loc*\
Ustawienia regionalne zawierające znak do przekonwertowania.

### <a name="return-value"></a>Wartość zwracana

Znak konwertowany na małe litery.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [ToLower](../standard-library/ctype-class.md#tolower)( `Ch` ).

### <a name="example"></a>Przykład

```cpp
// locale_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = tolower ( 'H', loc );
   cout << "The lower case of 'H' in the locale is: "
        << result1 << "." << endl;
   char result2 = tolower ( 'h', loc );
   cout << "The lower case of 'h' in the locale is: "
        << result2 << "." << endl;
   char result3 = tolower ( '$', loc );
   cout << "The lower case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="toupper"></a><a name="toupper"></a> ToUpper

Konwertuje znak do wielkiej litery.

```cpp
template <class CharType>
CharType toupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak do przekonwertowania na wielkie litery.

*Loc*\
Ustawienia regionalne zawierające znak do przekonwertowania.

### <a name="return-value"></a>Wartość zwracana

Znak konwertowany na wielkie litery.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [ToUpper](../standard-library/ctype-class.md#toupper)( `Ch` ).

### <a name="example"></a>Przykład

```cpp
// locale_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = toupper ( 'h', loc );
   cout << "The upper case of 'h' in the locale is: "
        << result1 << "." << endl;
   char result2 = toupper ( 'H', loc );
   cout << "The upper case of 'H' in the locale is: "
        << result2 << "." << endl;
   char result3 = toupper ( '$', loc );
   cout << "The upper case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="use_facet"></a><a name="use_facet"></a> use_facet

Zwraca odwołanie do zestawu reguł określonego typu przechowywanego w ustawieniach regionalnych.

```cpp
template <class Facet>
const Facet& use_facet(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Wartości ustawień stałych zawierających Typ zestawu reguł, którego dotyczy odwołanie.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do aspektu klasy `Facet` zawartej w ustawieniach regionalnych argumentu.

### <a name="remarks"></a>Uwagi

Odwołanie do aspektu zwróconego przez funkcję szablonu pozostaje prawidłowe, o ile istnieje jakakolwiek kopia zawierającej ją ustawień regionalnych. Jeśli w ustawieniach regionalnych argumentu nie ma takiego obiektu aspektu klasy `Facet` , funkcja zgłasza `bad_cast` wyjątek.

### <a name="example"></a>Przykład

```cpp
// locale_use_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );
   bool result1 = use_facet<ctype<char> > ( loc1 ).is(
   ctype_base::alpha, 'a'
);
   bool result2 = use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!'
   );

   if ( result1 )
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if ( result2 )
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;
}
```

```Output
The character 'a' in locale loc1 is alphabetic.
The character '!' in locale loc2 is not alphabetic.
```

## <a name="see-also"></a>Zobacz też

[\<locale>](../standard-library/locale.md)

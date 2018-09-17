---
title: '&lt;Ustawienia regionalne&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: c92f4f845552f5f6c14adb08191f1bd0519c7ba9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712455"
---
# <a name="ltlocalegt-functions"></a>&lt;Ustawienia regionalne&gt; funkcji

||||
|-|-|-|
|[has_facet](#has_facet)|[isalnum](#isalnum)|[isalpha](#isalpha)|
|[iscntrl](#iscntrl)|[isdigit](#isdigit)|[isgraph](#isgraph)|
|[islower](#islower)|[isprint](#isprint)|[ispunct](#ispunct)|
|[isspace](#isspace)|[isupper](#isupper)|[isxdigit](#isxdigit)|
|[tolower](#tolower)|[toupper](#toupper)|[use_facet](#use_facet)|

## <a name="has_facet"></a>  has_facet

Sprawdza, czy określony zestaw reguł jest przechowywany w określonych ustawieniach regionalnych.

```cpp
template <class Facet>
bool has_facet(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Lokalizacja*<br/>
Ustawienia regionalne pod kątem obecności zestaw reguł.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli ustawienia regionalne aspekt sprawdzane pod kątem; **false** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest przydatne w przypadku sprawdzania, czy nonmandatory zestawów reguł są wymienione w ustawieniach regionalnych przed `use_facet` jest wywoływana w celu uniknięcia wyjątek, który może zostać wygenerowany, jeśli nie był obecny.

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

## <a name="isalnum"></a>  isalnum

Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfabetycznym czy liczbowym.

```cpp
template <class CharType>
bool isalnum(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Element alfanumeryczne, które ma zostać przetestowana.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierający element alfanumeryczne, które ma zostać przetestowana.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** przypadku alfanumeryczne; badanego elementu **false** Jeśli tak nie jest.

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

## <a name="isalpha"></a>  isalpha

Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfabetycznym.

```cpp
template <class CharType>
bool isalpha(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Element, który ma zostać przetestowana.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierający element alfabetyczne, które ma zostać przetestowana.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** przypadku alfabetycznej; badanego elementu **false** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [jest](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **alfa**, `Ch`).

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

## <a name="iscntrl"></a>  iscntrl

Sprawdza, czy element w ustawieniach regionalnych jest znakiem kontrolnym.

```cpp
template <class CharType>
bool iscntrl(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Element, który ma zostać przetestowana.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierający element, który ma zostać przetestowana.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli badanego elementu jest znakiem kontrolnym; **false** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [jest](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **nacisnąć klawisze CTRL +**, `Ch`).

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

## <a name="isdigit"></a>  isdigit

Sprawdza, czy element w ustawieniach regionalnych jest znakiem liczbowym.

```cpp
template <class CharType>
bool isdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Element, który ma zostać przetestowana.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierający element, który ma zostać przetestowana.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli badanego elementu jest znakiem liczbowym; **false** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [jest](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **cyfrę**, `Ch`).

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

## <a name="isgraph"></a>  isgraph

Sprawdza, czy element w ustawieniach regionalnych jest znakiem alfanumerycznym lub interpunkcyjnym.

```cpp
template <class CharType>
bool isgraph(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Element, który ma zostać przetestowana.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierający element, który ma zostać przetestowana.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** przypadku badanego elementu alfanumerycznym lub znakiem interpunkcyjnym; **false** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [jest](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **wykres**, `Ch`).

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

## <a name="islower"></a>  islower

Sprawdza, czy element w ustawieniach regionalnych jest pisany małymi literami.

```cpp
template <class CharType>
bool islower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Element, który ma zostać przetestowana.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierający element, który ma zostać przetestowana.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli badanego elementu jest znakiem małej litery; **false** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [jest](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **niższe**, `Ch`).

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

## <a name="isprint"></a>  isprint

Sprawdza, czy element w ustawieniach regionalnych jest znakiem drukowalnym.

```cpp
template <class CharType>
bool isprint(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Element, który ma zostać przetestowana.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierający element, który ma zostać przetestowana.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli badanego elementu jest drukowalnym; **false** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [jest](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **drukowanie**, `Ch`).

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

## <a name="ispunct"></a>  ispunct

Sprawdza, czy element w ustawieniach regionalnych jest znakiem interpunkcyjnym.

```cpp
template <class CharType>
bool ispunct(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Element, który ma zostać przetestowana.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierający element, który ma zostać przetestowana.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli badanego elementu jest znakiem interpunkcyjnym; **false** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [use_facet](../standard-library/locale-functions.md#use_facet)`<`[ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [jest](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **punct**, `Ch`).

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

## <a name="isspace"></a>  isspace

Sprawdza, czy element w ustawieniach regionalnych jest znakiem białym.

```cpp
template <class CharType>
bool isspace(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Element, który ma zostać przetestowana.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierający element, który ma zostać przetestowana.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** przypadku badanego elementu znakiem odstępu; **false** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [jest](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **miejsca**, `Ch`).

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

## <a name="isupper"></a>  isupper

Sprawdza, czy element w ustawieniach regionalnych jest pisany wielkimi literami.

```cpp
template <class CharType>
bool isupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Element, który ma zostać przetestowana.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierający element, który ma zostać przetestowana.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli badanego elementu jest znakiem wielkiej litery; **false** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [jest](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **górny**, `Ch`).

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

## <a name="isxdigit"></a>  isxdigit

Sprawdza, czy element w ustawieniach regionalnych jest znakiem używanym do reprezentowania liczby w postaci szesnastkowej.

```cpp
template <class CharType>
bool isxdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Element, który ma zostać przetestowana.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierający element, który ma zostać przetestowana.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli badanego elementu jest znakiem używanym do reprezentowania liczby szesnastkowej; **false** Jeśli tak nie jest.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [jest](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **xdigit**, `Ch`).

Cyfry szesnastkowe użyć podstawowa 16 do reprezentowania liczb, przy użyciu cyfr od 0 do 9 oraz bez uwzględniania wielkości liter litery od A do F, aby reprezentować separatora dziesiętnego liczby od 0 do 15.

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

## <a name="tolower"></a>  tolower

Konwertuje znak do małej litery.

```cpp
template <class CharType>
CharType tolower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak, który ma zostać przekonwertowany na małe litery.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierającą znak, który ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Znak jest konwertowany na małe litery.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [tolower](../standard-library/ctype-class.md#tolower)( `Ch`).

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

## <a name="toupper"></a>  toupper

Konwertuje znak do wielkiej litery.

```cpp
template <class CharType>
CharType toupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak, który ma zostać przekonwertowany na wielkie litery.

*Lokalizacja*<br/>
Ustawienia regionalne, zawierającą znak, który ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Znak jest konwertowany na wielkie litery.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [toupper](../standard-library/ctype-class.md#toupper)( `Ch`).

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

## <a name="use_facet"></a>  use_facet

Zwraca odwołanie do zestawu reguł określonego typu przechowywanego w ustawieniach regionalnych.

```cpp
template <class Facet>
const Facet& use_facet(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Lokalizacja*<br/>
Const ustawienia regionalne, zawierający typ zestawu reguł, do którego nastąpiło odwołanie.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zestawu reguł klasy `Facet` zawartych w ustawieniach regionalnych argumentu.

### <a name="remarks"></a>Uwagi

Odwołanie do zestawu reguł, zwrócona przez funkcję szablonu zachowuje ważność tak długo, jak istnieje ewentualnych kopii zawierającego ustawienia regionalne. Jeśli nie ma takiego obiektu aspekt klasy `Facet` znajduje się w ustawieniach regionalnych argumentu, zgłasza funkcja `bad_cast` wyjątku.

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

## <a name="see-also"></a>Zobacz także

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>

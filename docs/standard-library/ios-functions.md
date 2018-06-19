---
title: '&lt;IOS&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- xiosbase/std::defaultfloat
- xiosbase/std::boolalpha
- xiosbase/std::dec
- ios/std::fixed
- ios/std::hex
- ios/std::internal
- ios/std::left
- ios/std::noboolalpha
- ios/std::noshowbase
- ios/std::noshowpoint
- ios/std::noshowpos
- ios/std::noskipws
- ios/std::nounitbuf
- ios/std::nouppercase
- ios/std::oct
- ios/std::right
- ios/std::scientific
- ios/std::showbase
- ios/std::showpoint
- ios/std::showpos
- ios/std::skipws
- ios/std::unitbuf
- ios/std::uppercase
ms.assetid: 1382d53f-e531-4b41-adf6-6a1543512e51
helpviewer_keywords:
- std::defaultfloat [C++]
- std::boolalpha [C++]
- std::dec [C++]
- std::fixed [C++]
- std::hex [C++]
- std::internal [C++]
- std::left [C++]
- std::noboolalpha [C++]
- std::noshowbase [C++]
- std::noshowpoint [C++]
- std::noshowpos [C++]
- std::noskipws [C++]
- std::nounitbuf [C++]
- std::nouppercase [C++]
- std::oct [C++]
- std::right [C++]
- std::scientific [C++]
- std::showbase [C++]
- std::showpoint [C++]
- std::showpos [C++]
- std::skipws [C++]
- std::unitbuf [C++]
- std::uppercase [C++]
ms.openlocfilehash: 4937d79c04484dd0cd96f74abb7150873b6f7235
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848427"
---
# <a name="ltiosgt-functions"></a>&lt;IOS&gt; funkcji

||||
|-|-|-|
|[defaultfloat —](#ios_defaultfloat)|[boolalpha](#boolalpha)|[DEC](#dec)|
|[Stałe](#fixed)|[hex](#hex)|[internal](#internal)|
|[left](#left)|[noboolalpha](#noboolalpha)|[noshowbase](#noshowbase)|
|[noshowpoint](#noshowpoint)|[noshowpos](#noshowpos)|[noskipws](#noskipws)|
|[nounitbuf](#nounitbuf)|[nouppercase](#nouppercase)|[oct](#oct)|
|[right](#right)|[scientific](#scientific)|[showbase](#showbase)|
|[showpoint](#showpoint)|[showpos](#showpos)|[skipws](#skipws)|
|[unitbuf](#unitbuf)|[wielkie litery](#uppercase)|

## <a name="boolalpha"></a>  boolalpha

Określa, że zmienne typu [bool](../cpp/bool-cpp.md) są wyświetlane jako **true** lub **false** w strumieniu.

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Domyślnie zmienne typu `bool` są wyświetlane jako 1 lub 0.

`boolalpha` wywołuje `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::boolalpha`), a następnie zwraca `str`.

[noboolalpha](../standard-library/ios-functions.md#noboolalpha) odwraca efekt `boolalpha`.

### <a name="example"></a>Przykład

```cpp
// ios_boolalpha.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   bool b = true;
   cout << b << endl;
   boolalpha( cout );
   cout << b << endl;
   noboolalpha( cout );
   cout << b << endl;
   cout << boolalpha << b << endl;
}
```

```Output
1
true
1
true
```

## <a name="dec"></a>  DEC

Określa, czy liczba całkowita zmienne są widoczne w podstawowej notacji 10.

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Domyślnie zmienne całkowitą są wyświetlane w podstawie 10.

**DEC** wywołuje `str.` [setf](../standard-library/ios-base-class.md#setf)( `ios_base::dec` **, ios_base::basefield**), a następnie zwraca `str`.

### <a name="example"></a>Przykład

```cpp
// ios_dec.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 100;

   cout << i << endl;   // Default is base 10
   cout << hex << i << endl;
   dec( cout );
   cout << i << endl;
   oct( cout );
   cout << i << endl;
   cout << dec << i << endl;
}
```

```Output
100
64
100
144
100
```

## <a name="ios_defaultfloat"></a>  &lt;IOS&gt; defaultfloat —

Konfiguruje flagi z `ios_base` obiekt, aby użyć domyślnego formatu wyświetlania dla wartości typu float.

```cpp
ios_base& defaultfloat(ios_base& _Iosbase);
```

### <a name="parameters"></a>Parametry

`_Iosbase` `ios_base` Obiektu.

### <a name="remarks"></a>Uwagi

Manipulatora wywołuje _znam `osbase.` [ios_base::unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`, następnie zwraca _znam `osbase`.

## <a name="fixed"></a>  Stałe

Określa, że liczba zmiennoprzecinkowa jest wyświetlana w notacji stałej dziesiętnej.

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

**stałe** jest notacji wyświetlana domyślna dla liczb zmiennoprzecinkowych. [Scientific](../standard-library/ios-functions.md#scientific) powoduje, że liczb zmiennoprzecinkowych będzie wyświetlana w notacji wykładniczej.

Wywołuje manipulatora * str.*[setf](../standard-library/ios-base-class.md#setf)( `ios_base::fixed`, **ios_base::floatfield**), a następnie zwraca `str`.

### <a name="example"></a>Przykład

```cpp
// ios_fixed.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 1.1F;

   cout << i << endl;   // fixed is the default
   cout << scientific << i << endl;
   cout.precision( 1 );
   cout << fixed << i << endl;
}
```

```Output
1.1
1.100000e+000
1.1
```

## <a name="hex"></a>  Hex

Określa, że liczba całkowita zmienne są są w podstawowej notacji 16.

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Domyślnie zmienne całkowitą są wyświetlane w notacji 10 podstawowej. [DEC](../standard-library/ios-functions.md#dec) i [oct](../standard-library/ios-functions.md#oct) również zmiany są wyświetlane zmienne całkowitą sposób.

Wywołuje manipulatora `str` **.** [setf](../standard-library/ios-base-class.md#setf)( `ios_base::hex`, **ios_base::basefield**), a następnie zwraca `str`.

### <a name="example"></a>Przykład

Zobacz [gru](../standard-library/ios-functions.md#dec) przykład sposobu użycia **szesnastkowych**.

## <a name="internal"></a>  wewnętrzny

Powoduje, że liczba Zaloguj, aby być wyrównane do lewej oraz numer do prawej.

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego `str` pochodzi.

### <a name="remarks"></a>Uwagi

[showpos](../standard-library/ios-functions.md#showpos) powoduje, że znak wyświetlany w przypadku liczby dodatnie.

Wywołuje manipulatora `str`. [SETF](../standard-library/ios-base-class.md#setf)( [ios_base::internal](../standard-library/ios-base-class.md#fmtflags), [ios_base::adjustfield](../standard-library/ios-base-class.md#fmtflags)), a następnie zwraca `str`.

### <a name="example"></a>Przykład

```cpp
// ios_internal.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( void )
{
   using namespace std;
   float i = -123.456F;
   cout.fill( '.' );
   cout << setw( 10 ) << i << endl;
   cout << setw( 10 ) << internal << i << endl;
}
```

```Output
..-123.456
-..123.456
```

## <a name="left"></a>  Po lewej

Powoduje, że tekst, który nie jest szerokie, jak szerokość dane wyjściowe mają być widoczne w opróżnienia strumienia do lewego marginesu.

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Wywołuje manipulatora `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::left`, **ios_base::adjustfield**), a następnie zwraca `str`.

### <a name="example"></a>Przykład

```cpp
// ios_left.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout.width( 20 );
   cout << f1 << endl;
   cout << left << f1 << endl;
}
```

```Output
                   5
5
```

## <a name="noboolalpha"></a>  noboolalpha

Określa, że zmienne typu [bool](../cpp/bool-cpp.md) są wyświetlane jako 1 lub 0 w strumieniu.

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Domyślnie `noboolalpha` jest włączona.

`noboolalpha` wywołuje `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::boolalpha`), a następnie zwraca `str`.

[boolalpha](../standard-library/ios-functions.md#boolalpha) odwraca efekt `noboolalpha`.

### <a name="example"></a>Przykład

Zobacz [boolalpha](../standard-library/ios-functions.md#boolalpha) przykład przy użyciu `noboolalpha`.

## <a name="noshowbase"></a>  noshowbase

Wyłącza wskazujący base notational, w którym jest wyświetlany numer.

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Domyślnie opcja `noshowbase` jest włączona. Użyj [showbase](../standard-library/ios-functions.md#showbase) wskazująca notational base liczb.

Wywołuje manipulatora `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::showbase`), a następnie zwraca `str`.

### <a name="example"></a>Przykład

Zobacz [showbase](../standard-library/ios-functions.md#showbase) przykład sposobu użycia `noshowbase`.

## <a name="noshowpoint"></a>  noshowpoint

Wyświetla tylko część liczby całkowitej liczby zmiennoprzecinkowe, których część ułamkowa wynosi zero.

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

`noshowpoint` jest on domyślnie; Użyj [showpoint](../standard-library/ios-functions.md#showpoint) i [dokładności](../standard-library/ios-base-class.md#precision) do wyświetlenia zerami po punkcie dziesiętnym.

Wywołuje manipulatora `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::showpoint`), a następnie zwraca `str`.

### <a name="example"></a>Przykład

```cpp
// ios_noshowpoint.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.000;
   cout << f1 << endl;   // noshowpoint is default
   cout.precision( 4 );
   cout << showpoint << f1 << endl;
   cout << noshowpoint << f1 << endl;
}
```

```Output
5
5.000
5
```

## <a name="noshowpos"></a>  noshowpos

Powoduje, że dodatnie nie jawnie były podpisane.

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Domyślnie opcja `noshowpos` jest włączona.

Wywołuje manipulatora `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::showps`), zwraca `str`.

### <a name="example"></a>Przykład

Zobacz [showpos](../standard-library/ios-functions.md#showpos) przykład przy użyciu `noshowpos`.

## <a name="noskipws"></a>  noskipws

Spowodować spacje odczytywane przez strumień wejściowy.

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Domyślnie [skipws](../standard-library/ios-functions.md#skipws) jest włączona. Przeczytaniu odstęp w strumieniu wejściowym sygnalizuje koniec buforu.

Wywołuje manipulatora `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::skipws`), a następnie zwraca `str`.

### <a name="example"></a>Przykład

```cpp
// ios_noskipws.cpp
// compile with: /EHsc
#include <iostream>
#include <string>

int main() {
   using namespace std;
   string s1, s2, s3;
   cout << "Enter three strings: ";
   cin >> noskipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

## <a name="nounitbuf"></a>  nounitbuf

Powoduje, że dane wyjściowe buforowane i przetwarzane na, gdy bufor jest pełna.

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

[unitbuf](../standard-library/ios-functions.md#unitbuf) powoduje, że bufor do przetwarzania, gdy nie jest pusty.

Wywołuje manipulatora `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::unitbuf`), a następnie zwraca `str`.

## <a name="nouppercase"></a>  nouppercase

Określa, że cyfr szesnastkowych i wykładnik w notacji naukowej są pisane małymi literami.

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Wywołuje manipulatora `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::uppercase`), a następnie zwraca `str`.

### <a name="example"></a>Przykład

Zobacz [wielkich](../standard-library/ios-functions.md#uppercase) przykład przy użyciu `nouppercase`.

## <a name="oct"></a>  OCT

Określa, czy liczba całkowita zmienne są widoczne w podstawowej notacji 8.

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego *str* pochodzi.

### <a name="remarks"></a>Uwagi

Domyślnie zmienne całkowitą są wyświetlane w notacji 10 podstawowej. [DEC](../standard-library/ios-functions.md#dec) i [szesnastkowych](../standard-library/ios-functions.md#hex) również zmiany są wyświetlane zmienne całkowitą sposób.

Wywołuje manipulatora `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::oct`, `ios_base::basefield`), a następnie zwraca `str`.

### <a name="example"></a>Przykład

Zobacz [gru](../standard-library/ios-functions.md#dec) przykład sposobu użycia **oct**.

## <a name="right"></a>  Prawo

Powoduje, że tekst, który nie jest szerokie, jak szerokość dane wyjściowe mają być widoczne w opróżnienia strumienia do prawego marginesu.

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego *str* pochodzi.

### <a name="remarks"></a>Uwagi

[po lewej stronie](../standard-library/ios-functions.md#left) także modyfikuje Justowanie tekstu.

Wywołuje manipulatora `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::right`, `ios_base::adjustfield`), a następnie zwraca `str`.

### <a name="example"></a>Przykład

```cpp
// ios_right.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << left << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << right << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
}
```

```Output
5
                   5
5
5
                   5
                   5
```

## <a name="scientific"></a>  Naukowe

Liczby zmiennoprzecinkowe powoduje, że mają być wyświetlane w notacji wykładniczej.

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Domyślnie [stałej](../standard-library/ios-functions.md#fixed) notacji są włączone dla liczb zmiennoprzecinkowych.

Wywołuje manipulatora `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::scientific`, `ios_base::floatfield`), a następnie zwraca `str`.

### <a name="example"></a>Przykład

```cpp
// ios_scientific.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 100.23F;

   cout << i << endl;
   cout << scientific << i << endl;
}
```

```Output
100.23
1.002300e+002
```

## <a name="showbase"></a>  showbase

Wskazuje podstawowy notational, w którym jest wyświetlany numer.

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Notational base liczby można zmienić z [gru](../standard-library/ios-functions.md#dec), [oct](../standard-library/ios-functions.md#oct), lub [szesnastkowych](../standard-library/ios-functions.md#hex).

Wywołuje manipulatora `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::showbase`), a następnie zwraca `str`.

### <a name="example"></a>Przykład

```cpp
// ios_showbase.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int j = 100;

   cout << showbase << j << endl;   // dec is default
   cout << hex << j << showbase << endl;
   cout << oct << j << showbase << endl;

   cout << dec << j << noshowbase << endl;
   cout << hex << j << noshowbase << endl;
   cout << oct << j << noshowbase << endl;
}
```

```Output
100
0x64
0144
100
64
144
```

## <a name="showpoint"></a>  showpoint

Wyświetla część liczby całkowitej liczbie zmiennoprzecinkowej i cyfr z prawej strony punktu dziesiętnego nawet wtedy, gdy część ułamkowa wynosi zero.

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Domyślnie [noshowpoint](../standard-library/ios-functions.md#noshowpoint) jest włączona.

Wywołuje manipulatora `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::showpoint`), a następnie zwraca `str`.

### <a name="example"></a>Przykład

Zobacz [noshowpoint](../standard-library/ios-functions.md#noshowpoint) przykład przy użyciu `showpoint`.

## <a name="showpos"></a>  showpos

Powoduje, że dodatnie jawnie były podpisane.

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

[noshowpos](../standard-library/ios-functions.md#noshowpos) jest ustawieniem domyślnym.

Wywołuje manipulatora `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::showpos`), a następnie zwraca `str`.

### <a name="example"></a>Przykład

```cpp
// ios_showpos.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 1;

   cout << noshowpos << i << endl;   // noshowpos is default
   cout << showpos << i << endl;
}
```

```Output
1
+1
```

## <a name="skipws"></a>  skipws

Spowodować spacje nie można odczytać strumienia wejściowego.

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którym _ *Str* pochodzi.

### <a name="remarks"></a>Uwagi

Domyślnie `skipws` jest włączona. [noskipws](../standard-library/ios-functions.md#noskipws) spowoduje, że spacje Odczyt ze strumienia wejściowego.

Wywołuje manipulatora `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::skipws`), a następnie zwraca `str`.

### <a name="example"></a>Przykład

```cpp
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   char s1, s2, s3;
   cout << "Enter three characters: ";
   cin >> skipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

```Output

1 2 3

```

```Output

      1 2 3.1.
.2.
.3.
```

## <a name="unitbuf"></a>  unitbuf

Powoduje, że dane wyjściowe do przetworzenia, gdy bufor nie jest pusty.

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego `str` pochodzi.

### <a name="remarks"></a>Uwagi

Należy pamiętać, że `endl` również opróżnia bufor.

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) jest włączona domyślnie.

Wywołuje manipulatora `str`.[ SETF](../standard-library/ios-base-class.md#setf)( [ios_base::unitbuf](../standard-library/ios-base-class.md#fmtflags)), a następnie zwraca `str`.

## <a name="uppercase"></a>  wielkie litery

Określa, że cyfr szesnastkowych i wykładnik w notacji naukowej są pisane wielkimi literami.

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odwołanie do obiektu typu [ios_base —](../standard-library/ios-base-class.md), lub do typu, który dziedziczy `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego `str` pochodzi.

### <a name="remarks"></a>Uwagi

Domyślnie [nouppercase](../standard-library/ios-functions.md#nouppercase) jest włączona.

Wywołuje manipulatora `str`.[ SETF](../standard-library/ios-base-class.md#setf)( [ios_base::uppercase](../standard-library/ios-base-class.md#fmtflags)), a następnie zwraca `str`.

### <a name="example"></a>Przykład

```cpp
// ios_uppercase.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
   using namespace std;

   double i = 1.23e100;
   cout << i << endl;
   cout << uppercase << i << endl;

   int j = 10;
   cout << hex << nouppercase << j << endl;
   cout << hex << uppercase << j << endl;
}
```

```Output
1.23e+100
1.23E+100
a
A
```

## <a name="see-also"></a>Zobacz także

[\<IOS >](../standard-library/ios.md)<br/>

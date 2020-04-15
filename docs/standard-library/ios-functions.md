---
title: '&lt;funkcje&gt; ios'
ms.date: 11/04/2016
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
- std::hexfloat [C++]
- std::io_errc [C++]
- std::internal [C++]
- std::iostream_category [C++]
- std::is_error_code_enum [C++]
- std::left [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
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
ms.openlocfilehash: 67ac9259110abbd03fc054ea4e60ed1715030dcc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375416"
---
# <a name="ltiosgt-functions"></a>&lt;funkcje&gt; ios

## <a name="boolalpha"></a><a name="boolalpha"></a>boolalpha

Określa, że zmienne typu [bool](../cpp/bool-cpp.md) są wyświetlane jako **prawdziwe** lub **fałszywe** w strumieniu.

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Domyślnie zmienne typu **bool** są wyświetlane jako 1 lub 0.

`boolalpha`skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)( `ios_base::boolalpha`), a następnie zwraca *str*.

[noboolalpha](../standard-library/ios-functions.md#noboolalpha) odwraca działanie `boolalpha`.

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

## <a name="dec"></a><a name="dec"></a>Grudnia

Określa, że zmienne całkowite są wyświetlane w notacji podstawowej 10.

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Domyślnie zmienne całkowite są wyświetlane w podstawowej 10.

`dec`skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)( `ios_base::dec`, `ios_base::basefield`), a następnie zwraca *str*.

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

## <a name="ltiosgt-defaultfloat"></a><a name="ios_defaultfloat"></a>&lt;ios&gt; defaultfloat

Konfiguruje flagi `ios_base` obiektu, aby używać domyślnego formatu wyświetlania dla wartości zmiennoprzec pływakowych.

```cpp
ios_base& defaultfloat(ios_base& iosbase);
```

### <a name="parameters"></a>Parametry

*_Iosbase*\
Obiekt `ios_base`.

### <a name="remarks"></a>Uwagi

Manipulator skutecznie `iosbase.`wywołuje [ios_base::unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`, a następnie zwraca *iosbase*.

## <a name="fixed"></a><a name="fixed"></a>Stałe

Określa, że liczba zmiennoprzecinkowa jest wyświetlana w notacji o stałym przecinku.

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

`fixed`jest domyślną notacją wyświetlania dla liczb zmiennoprzecinkowych. [naukowe](../standard-library/ios-functions.md#scientific) powoduje, że liczby zmiennoprzecinkowe mają być wyświetlane przy użyciu notacji naukowej.

Manipulator skutecznie wywołuje *str*. [setf](../standard-library/ios-base-class.md#setf) `ios_base::fixed`( `ios_base::floatfield` , ), a następnie zwraca *str*.

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

## <a name="hex"></a><a name="hex"></a>Hex

Określa, że zmienne całkowite pojawiają się w notacji podstawowej 16.

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Domyślnie zmienne całkowite są wyświetlane w notacji podstawowej 10. [dec](../standard-library/ios-functions.md#dec) i [oct](../standard-library/ios-functions.md#oct) również zmienić sposób pojawiania się zmiennych całkowitych.

Manipulator skutecznie `str`wywołuje **.** [setf](../standard-library/ios-base-class.md#setf) `ios_base::hex`( `ios_base::basefield`, ), a następnie zwraca *str*.

### <a name="example"></a>Przykład

Zobacz [dec](../standard-library/ios-functions.md#dec) na przykład jak `hex`używać .

## <a name="hexfloat"></a><a name="hexfloat"></a>heksfloat

```cpp
ios_base& hexfloat (ios_base& str);
```

## <a name="io_errc"></a><a name="io_errc"></a>io_errc

```cpp
enum class io_errc {
    stream = 1
};
```

## <a name="internal"></a><a name="internal"></a>Wewnętrznego

Powoduje, że znak liczby jest wyjustowany, a numer do prawej.

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

[showpos](../standard-library/ios-functions.md#showpos) powoduje, że znak jest wyświetlany dla liczb dodatnich.

Manipulator skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)`(`[ios_base::internal](../standard-library/ios-base-class.md#fmtflags) `,` [ios_base::adjustfield](../standard-library/ios-base-class.md#fmtflags)`)`, a następnie zwraca *str*.

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

## <a name="is_error_code_enum"></a><a name="is_error_code_enum"></a>is_error_code_enum

```cpp
template <> struct is_error_code_enum<io_errc> : public true_type { };
```

## <a name="iostream_category"></a><a name="iostream_category"></a>iostream_category

```cpp
const error_category& iostream_category() noexcept;
```

## <a name="left"></a><a name="left"></a>Lewej

Powoduje, że tekst, który nie jest tak szeroki, jak szerokość wyjściowa, aby pojawić się w strumieniu równo z lewym marginesem.

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Manipulator skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)`(ios_base::left, ios_base::adjustfield)`, a następnie zwraca *str*.

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

## <a name="make_error_code"></a><a name="make_error_code"></a>make_error_code

```cpp
error_code make_error_code(io_errc e) noexcept;
```

## <a name="make_error_condition"></a><a name="make_error_condition"></a>make_error_condition

```cpp
error_condition make_error_condition(io_errc e) noexcept;
```

## <a name="noboolalpha"></a><a name="noboolalpha"></a>noboolalpha ( noboolalpha )

Określa, że zmienne typu [bool](../cpp/bool-cpp.md) są wyświetlane jako 1 lub 0 w strumieniu.

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Domyślnie `noboolalpha` obowiązuje.

`noboolalpha`skutecznie `str.`wywołuje [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::boolalpha)`, a następnie zwraca *str*.

[boolalpha](../standard-library/ios-functions.md#boolalpha) odwraca działanie `noboolalpha`.

### <a name="example"></a>Przykład

Zobacz [boolalpha](../standard-library/ios-functions.md#boolalpha) na przykład `noboolalpha`za pomocą .

## <a name="noshowbase"></a><a name="noshowbase"></a>noshowbase

Wyłącza się wskazując bazę notacyjną, w której wyświetlana jest liczba.

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Domyślnie opcja `noshowbase` jest włączona. Użyj [showbase,](../standard-library/ios-functions.md#showbase) aby wskazać wartość notacyjną liczb.

Manipulator skutecznie `str.`wywołuje [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showbase)`, a następnie zwraca *str*.

### <a name="example"></a>Przykład

Zobacz [showbase](../standard-library/ios-functions.md#showbase) na przykład, `noshowbase`jak używać .

## <a name="noshowpoint"></a><a name="noshowpoint"></a>noshowpoint

Wyświetla tylko całą liczbę liczb zmiennoprzecinkowych, których część ułamkowa wynosi zero.

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

`noshowpoint`jest domyślnie włączony; użyj [punktu pokazowego](../standard-library/ios-functions.md#showpoint) i [precyzji,](../standard-library/ios-base-class.md#precision) aby wyświetlić zera po przecinku.

Manipulator skutecznie `str.`wywołuje [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showpoint)`, a następnie zwraca *str*.

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

## <a name="noshowpos"></a><a name="noshowpos"></a>noshowpos

Powoduje, że liczby dodatnie nie są jawnie podpisane.

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Domyślnie opcja `noshowpos` jest włączona.

Manipulator skutecznie `str.`wywołuje [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showps)`, a następnie zwraca *str*.

### <a name="example"></a>Przykład

Zobacz [showpos](../standard-library/ios-functions.md#showpos) na przykład `noshowpos`za pomocą .

## <a name="noskipws"></a><a name="noskipws"></a>noskipws (noskipws)

Spowodować spacji do odczytu przez strumień wejściowy.

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Domyślnie [skipws](../standard-library/ios-functions.md#skipws) jest w mocy. Gdy spacja jest odczytywana w strumieniu wejściowym, sygnalizuje koniec buforu.

Manipulator skutecznie `str.`wywołuje [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::skipws)`, a następnie zwraca *str*.

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

## <a name="nounitbuf"></a><a name="nounitbuf"></a>nounitbuf

Powoduje, że dane wyjściowe mają być buforowane i przetwarzane na gdy bufor jest pełny.

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

[unitbuf](../standard-library/ios-functions.md#unitbuf) powoduje, że bufor ma być przetwarzany, gdy nie jest pusty.

Manipulator skutecznie `str.`wywołuje [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::unitbuf)`, a następnie zwraca *str*.

## <a name="nouppercase"></a><a name="nouppercase"></a>nouppercase (wask nouppercase)

Określa, że cyfry szesnastkowe i wykładnik w notacji naukowej są wyświetlane w małych literach.

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Manipulator skutecznie `str.`wywołuje [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::uppercase)`, a następnie zwraca *str*.

### <a name="example"></a>Przykład

Zobacz [wielkie litery,](../standard-library/ios-functions.md#uppercase) aby `nouppercase`uzyskać przykład użycia .

## <a name="oct"></a><a name="oct"></a>Października

Określa, że zmienne całkowite są wyświetlane w notacji podstawowej 8.

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Domyślnie zmienne całkowite są wyświetlane w notacji podstawowej 10. [dec](../standard-library/ios-functions.md#dec) i [hex](../standard-library/ios-functions.md#hex) również zmienić sposób pojawiania się zmiennych całkowitych.

Manipulator skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)`(ios_base::oct, ios_base::basefield)`, a następnie zwraca *str*.

### <a name="example"></a>Przykład

Zobacz [dec](../standard-library/ios-functions.md#dec) na przykład jak `oct`używać .

## <a name="right"></a><a name="right"></a>Prawo

Powoduje, że tekst, który nie jest tak szeroki, jak szerokość wyjściowa, aby pojawić się w strumieniu równo z prawym marginesem.

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

[w lewo](../standard-library/ios-functions.md#left) również modyfikuje uzasadnienie tekstu.

Manipulator skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)`(ios_base::right, ios_base::adjustfield)`, a następnie zwraca *str*.

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

## <a name="scientific"></a><a name="scientific"></a>Naukowych

Powoduje, że liczby zmiennoprzecinkowe mają być wyświetlane przy użyciu notacji naukowej.

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Domyślnie [stała](../standard-library/ios-functions.md#fixed) notacja obowiązuje dla liczb zmiennoprzecinkowych.

Manipulator skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)`(ios_base::scientific, ios_base::floatfield)`, a następnie zwraca *str*.

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

## <a name="showbase"></a><a name="showbase"></a>baza pokazowa

Wskazuje podstawę notacyjną, w której wyświetlana jest liczba.

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Bazę notacyjną liczby można zmienić za pomocą [dec,](../standard-library/ios-functions.md#dec) [oct](../standard-library/ios-functions.md#oct)lub [hex](../standard-library/ios-functions.md#hex).

Manipulator skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)`(ios_base::showbase)`, a następnie zwraca *str*.

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

## <a name="showpoint"></a><a name="showpoint"></a>punkt pokazu

Wyświetla całą liczbę części liczby zmiennoprzecinkowej i cyfry po prawej stronie przecinka dziesiętnego, nawet jeśli część ułamkowa wynosi zero.

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Domyślnie [nieshowpoint](../standard-library/ios-functions.md#noshowpoint) jest w mocy.

Manipulator skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)`(ios_base::showpoint)`, a następnie zwraca *str*.

### <a name="example"></a>Przykład

Zobacz [noshowpoint](../standard-library/ios-functions.md#noshowpoint) na przykład `showpoint`za pomocą .

## <a name="showpos"></a><a name="showpos"></a>showpos

Powoduje, że liczby dodatnie mają być jawnie podpisane.

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

[noshowpos](../standard-library/ios-functions.md#noshowpos) jest domyślnym.

Manipulator skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)`(ios_base::showpos)`, a następnie zwraca *str*.

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

## <a name="skipws"></a><a name="skipws"></a>skipws (pomijanie)

Spowodować spacje nie są odczytywane przez strumień wejściowy.

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Domyślnie `skipws` obowiązuje. [noskipws](../standard-library/ios-functions.md#noskipws) spowoduje spacji do odczytu ze strumienia wejściowego.

Manipulator skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)`(ios_base::skipws)`, a następnie zwraca *str*.

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

```Input
1 2 3
```

```Output
Enter three characters: 1 2 3
.1.
.2.
.3.
```

## <a name="unitbuf"></a><a name="unitbuf"></a>unitbuf ( unitbuf )

Powoduje, że dane wyjściowe mają być przetwarzane, gdy bufor nie jest pusty.

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Należy `endl` zauważyć, że również opróżnia buforu.

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) jest w mocy domyślnie.

Manipulator skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)`(`[ios_base::unitbuf](../standard-library/ios-base-class.md#fmtflags)`)`, a następnie zwraca *str*.

## <a name="uppercase"></a><a name="uppercase"></a>Wielkie

Określa, że cyfry szesnastkowe i wykładnik w notacji naukowej są wyświetlane w małych literach.

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który `ios_base`dziedziczy po .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi *str.*

### <a name="remarks"></a>Uwagi

Domyślnie [nouppercase](../standard-library/ios-functions.md#nouppercase) jest w mocy.

Manipulator skutecznie `str.`wywołuje [setf](../standard-library/ios-base-class.md#setf)`(`[ios_base::wielkie litery](../standard-library/ios-base-class.md#fmtflags)`)`, a następnie zwraca *str*.

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

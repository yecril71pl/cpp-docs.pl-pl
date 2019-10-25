---
title: '&lt;funkcje&gt; systemu iOS'
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
ms.openlocfilehash: c3b1e2350d0923cbfddf95492842ae126859e29f
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890070"
---
# <a name="ltiosgt-functions"></a>&lt;funkcje&gt; systemu iOS

## <a name="boolalpha"></a>boolalpha

Określa, że zmienne typu [bool](../cpp/bool-cpp.md) są wyświetlane jako **true** lub **false** w strumieniu.

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Domyślnie zmienne typu **bool** są wyświetlane jako 1 lub 0.

`boolalpha` efektywne wywołania `str.`[setf](../standard-library/ios-base-class.md#setf)(`ios_base::boolalpha`), a następnie zwraca *str*.

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

## <a name="dec"></a>grudzień

Określa, że zmienne całkowite pojawiają się w notacji Base 10.

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Domyślnie zmienne typu integer są wyświetlane w podstawowym 10.

`dec` efektywne wywołania `str.`[setf](../standard-library/ios-base-class.md#setf)(`ios_base::dec`, `ios_base::basefield`), a następnie zwraca *str*.

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

## <a name="ios_defaultfloat"></a>&lt;iOS&gt; defaultfloat

Konfiguruje flagi obiektu `ios_base`, aby użyć domyślnego formatu wyświetlania wartości zmiennoprzecinkowych.

```cpp
ios_base& defaultfloat(ios_base& iosbase);
```

### <a name="parameters"></a>Parametry

*_Iosbase*\
Obiekt `ios_base`.

### <a name="remarks"></a>Uwagi

Manipulator skutecznie wywołuje `iosbase.`[ios_base:: unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`, a następnie zwraca *iosbase*.

## <a name="fixed"></a>FIXED

Określa, że liczba zmiennoprzecinkowa jest wyświetlana w notacji o stałej liczbie dziesiętnej.

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

`fixed` jest domyślnym notacją wyświetlania liczb zmiennoprzecinkowych. [naukowe](../standard-library/ios-functions.md#scientific) powoduje, że liczby zmiennoprzecinkowe będą wyświetlane przy użyciu notacji wykładniczej.

Manipulator skutecznie wywołuje *str*. [setf](../standard-library/ios-base-class.md#setf)(`ios_base::fixed`, `ios_base::floatfield`), a następnie zwraca *str*.

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

## <a name="hex"></a>szesnastkowy

Określa, że zmienne typu integer są wyświetlane w notacji Base 16.

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Domyślnie zmienne typu integer są wyświetlane w notacji Base 10. w [gru](../standard-library/ios-functions.md#dec) i [OCT](../standard-library/ios-functions.md#oct) zmieniono również sposób wyświetlania zmiennych liczb całkowitych.

Manipulator skutecznie wywołuje `str` **.** [setf](../standard-library/ios-base-class.md#setf)(`ios_base::hex`, `ios_base::basefield`), a następnie zwraca *str*.

### <a name="example"></a>Przykład

Zapoznaj [się](../standard-library/ios-functions.md#dec) z przykładem, jak korzystać z `hex`.

## <a name="hexfloat"></a>hexfloat

```cpp
ios_base& hexfloat (ios_base& str);
```

## <a name="io_errc"></a>io_errc

```cpp
enum class io_errc {
    stream = 1
};
```

## <a name="internal"></a>wewnętrz

Powoduje, że znak liczby jest wyrównany do lewej, a liczba powinna być wyrównana do prawej.

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

[showpos](../standard-library/ios-functions.md#showpos) powoduje, że znak jest wyświetlany dla liczb dodatnich.

Manipulator skutecznie wywołuje `str.`[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base:: Internal](../standard-library/ios-base-class.md#fmtflags)`, `[ios_base:: adjustfield](../standard-library/ios-base-class.md#fmtflags)`)`, a następnie zwraca *str*.

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

## <a name="is_error_code_enum"></a>is_error_code_enum

```cpp
template <> struct is_error_code_enum<io_errc> : public true_type { };
```

## <a name="iostream_category"></a>iostream_category

```cpp
const error_category& iostream_category() noexcept;
```

## <a name="left"></a>lewym

Powoduje, że tekst nie jest tak szeroki, jak szerokość danych wyjściowych, która ma być wyświetlana w strumieniu opróżniania z lewego marginesu.

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Manipulator skutecznie wywołuje `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::left, ios_base::adjustfield)`, a następnie zwraca *str*.

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

## <a name="make_error_code"></a>make_error_code

```cpp
error_code make_error_code(io_errc e) noexcept;
```

## <a name="make_error_condition"></a>make_error_condition

```cpp
error_condition make_error_condition(io_errc e) noexcept;
```

## <a name="noboolalpha"></a>noboolalpha

Określa, że zmienne typu [bool](../cpp/bool-cpp.md) są wyświetlane jako 1 lub 0 w strumieniu.

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Domyślnie `noboolalpha` jest włączona.

`noboolalpha` efektywne wywołania `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::boolalpha)`, a następnie zwraca *str*.

[boolalpha](../standard-library/ios-functions.md#boolalpha) odwraca efekt `noboolalpha`.

### <a name="example"></a>Przykład

Zobacz [boolalpha](../standard-library/ios-functions.md#boolalpha) , aby zapoznać się z przykładem korzystania z `noboolalpha`.

## <a name="noshowbase"></a>noshowbase

Wyłącza opcję wskazującą podstawę notacji, w której wyświetlana jest liczba.

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Domyślnie opcja `noshowbase` jest włączona. Użyj [showbase](../standard-library/ios-functions.md#showbase) , aby wskazać notację z numeracji.

Manipulator skutecznie wywołuje `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showbase)`, a następnie zwraca *str*.

### <a name="example"></a>Przykład

Zobacz [showbase](../standard-library/ios-functions.md#showbase) , aby zapoznać się z przykładem korzystania z `noshowbase`.

## <a name="noshowpoint"></a>noshowpoint

Wyświetla tylko liczbę całkowitą części liczb zmiennoprzecinkowych, których część ułamkowa ma wartość zero.

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

`noshowpoint` jest domyślnie włączona; Użyj [Showpoint](../standard-library/ios-functions.md#showpoint) i [Precision](../standard-library/ios-base-class.md#precision) , aby wyświetlić zera po przecinku dziesiętnym.

Manipulator skutecznie wywołuje `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showpoint)`, a następnie zwraca *str*.

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

## <a name="noshowpos"></a>noshowpos

Powoduje, że liczby dodatnie nie mogą być podpisywane jawnie.

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Domyślnie opcja `noshowpos` jest włączona.

Manipulator skutecznie wywołuje `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showps)`, a następnie zwraca *str*.

### <a name="example"></a>Przykład

Zobacz [showpos](../standard-library/ios-functions.md#showpos) , aby zapoznać się z przykładem korzystania z `noshowpos`.

## <a name="noskipws"></a>noskipws

Zapoznaj się z miejscem, w którym znajduje się strumień wejściowy.

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Domyślnie [skipws](../standard-library/ios-functions.md#skipws) jest włączone. Gdy spacja jest odczytywana w strumieniu wejściowym, sygnalizuje koniec buforu.

Manipulator skutecznie wywołuje `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::skipws)`, a następnie zwraca *str*.

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

## <a name="nounitbuf"></a>nounitbuf

Powoduje, że dane wyjściowe są buforowane i przetwarzane, gdy bufor jest pełny.

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

[unitbuf](../standard-library/ios-functions.md#unitbuf) powoduje, że bufor jest przetwarzany, gdy nie jest pusty.

Manipulator skutecznie wywołuje `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::unitbuf)`, a następnie zwraca *str*.

## <a name="nouppercase"></a>nowielkie litery

Określa, że cyfry szesnastkowe i wykładnik w notacji wykładniczej są wyświetlane małymi literami.

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Manipulator skutecznie wywołuje `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::uppercase)`, a następnie zwraca *str*.

### <a name="example"></a>Przykład

Przykład [](../standard-library/ios-functions.md#uppercase) użycia `nouppercase`.

## <a name="oct"></a>ósemkow

Określa, że zmienne całkowite pojawiają się w notacji Base 8.

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Domyślnie zmienne typu integer są wyświetlane w notacji Base 10. w [gru](../standard-library/ios-functions.md#dec) i [szesnastkowy](../standard-library/ios-functions.md#hex) zmieniają się sposób wyświetlania zmiennych liczb całkowitych.

Manipulator skutecznie wywołuje `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::oct, ios_base::basefield)`, a następnie zwraca *str*.

### <a name="example"></a>Przykład

Zapoznaj [się](../standard-library/ios-functions.md#dec) z przykładem, jak korzystać z `oct`.

## <a name="right"></a>Kliknij

Powoduje, że tekst nie jest tak szeroki, jak szerokość danych wyjściowych, która ma być wyświetlana w strumieniu opróżniania z prawego marginesu.

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

[po lewej](../standard-library/ios-functions.md#left) również modyfikuje uzasadnienie tekstu.

Manipulator skutecznie wywołuje `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::right, ios_base::adjustfield)`, a następnie zwraca *str*.

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

## <a name="scientific"></a>nauk

Powoduje wyświetlanie liczb zmiennoprzecinkowych przy użyciu notacji wykładniczej.

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Domyślnie [stała](../standard-library/ios-functions.md#fixed) notacja jest stosowana dla liczb zmiennoprzecinkowych.

Manipulator skutecznie wywołuje `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::scientific, ios_base::floatfield)`, a następnie zwraca *str*.

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

## <a name="showbase"></a>showbase

Wskazuje podstawę notacji, w której wyświetlana jest liczba.

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Podstawą zapisu liczby można zmienić za pomocą [gru](../standard-library/ios-functions.md#dec), [KTZ](../standard-library/ios-functions.md#oct)lub [szesnastkowych](../standard-library/ios-functions.md#hex).

Manipulator skutecznie wywołuje `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::showbase)`, a następnie zwraca *str*.

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

## <a name="showpoint"></a>showpoint

Wyświetla część liczby zmiennoprzecinkowej i cyfr z prawej strony punktu dziesiętnego, nawet jeśli część ułamkowa jest równa zero.

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Domyślnie [noshowpoint](../standard-library/ios-functions.md#noshowpoint) jest włączone.

Manipulator skutecznie wywołuje `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::showpoint)`, a następnie zwraca *str*.

### <a name="example"></a>Przykład

Zobacz [noshowpoint](../standard-library/ios-functions.md#noshowpoint) , aby zapoznać się z przykładem korzystania z `showpoint`.

## <a name="showpos"></a>showpos

Powoduje jawne podpisywanie liczb dodatnich.

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

wartość domyślna to [noshowpos](../standard-library/ios-functions.md#noshowpos) .

Manipulator skutecznie wywołuje `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::showpos)`, a następnie zwraca *str*.

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

## <a name="skipws"></a>skipws

Nie należy odczytywać spacji w strumieniu wejściowym.

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Domyślnie `skipws` jest włączona. [noskipws](../standard-library/ios-functions.md#noskipws) spowoduje odczytanie spacji ze strumienia wejściowego.

Manipulator skutecznie wywołuje `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::skipws)`, a następnie zwraca *str*.

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

## <a name="unitbuf"></a>unitbuf

Powoduje, że dane wyjściowe będą przetwarzane, gdy bufor nie jest pusty.

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Należy zauważyć, że `endl` opróżnia również bufor.

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) jest domyślnie włączona.

Manipulator skutecznie wywołuje `str.`[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base:: unitbuf](../standard-library/ios-base-class.md#fmtflags)`)`, a następnie zwraca *str*.

## <a name="uppercase"></a>znaki

Określa, że cyfry szesnastkowe i wykładnik w notacji wykładniczej są wyświetlane wielką literą.

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str* \
Odwołanie do obiektu typu [ios_base](../standard-library/ios-base-class.md)lub do typu, który dziedziczy z `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu, z którego pochodzi element *str* .

### <a name="remarks"></a>Uwagi

Domyślnie [wielkie litery](../standard-library/ios-functions.md#nouppercase) obowiązują.

Manipulator skutecznie wywołuje `str.`[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base:: wielkie](../standard-library/ios-base-class.md#fmtflags)`)`, a następnie zwraca *str*.

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

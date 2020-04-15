---
title: '&lt;funkcje iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::get_money
- iomanip/std::get_time
- iomanip/std::put_money
- iomanip/std::put_time
- iomanip/std::quoted
- iomanip/std::resetiosflags
- iomanip/std::setbase
- iomanip/std::setfill
- iomanip/std::setiosflags
- iomanip/std::setprecision
- iomanip/std::setw
ms.assetid: 3ddde610-70cc-4cfa-8a89-3e83d1d356a8
helpviewer_keywords:
- std::get_money [C++]
- std::get_time [C++]
- std::put_money [C++]
- std::put_time [C++]
- std::quoted [C++]
- std::resetiosflags [C++]
- std::setbase [C++]
- std::setfill [C++]
- std::setiosflags [C++]
- std::setprecision [C++]
- std::setw [C++]
ms.openlocfilehash: 0ed59a94c6b1c7d962b566e2a6b186ffb617a26a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375423"
---
# <a name="ltiomanipgt-functions"></a>&lt;funkcje iomanip&gt;

||||
|-|-|-|
|[get_money](#iomanip_get_money)|[get_time](#iomanip_get_time)|[put_money](#iomanip_put_money)|
|[put_time](#iomanip_put_time)|[Cytowany](#quoted)|[resetiosflags](#resetiosflags)|
|[baza setbase](#setbase)|[setfill (setfill)](#setfill)|[setiosflags](#setiosflags)|
|[setprecision (setprecision)](#setprecision)|[Setw](#setw)|

## <a name="get_money"></a><a name="iomanip_get_money"></a>get_money

Wyodrębnia wartość pieniężną ze strumienia przy użyciu żądanego formatu i zwraca wartość w parametrze.

```cpp
template <class Money>
T7 get_money(Money& amount, bool use_intl);
```

### <a name="parameters"></a>Parametry

*Kwota*\
Wydobyta wartość pieniężna.

*use_intl*\
Jeśli **true**, użyj formatu międzynarodowego. Wartość domyślna to **fałsz**.

### <a name="remarks"></a>Uwagi

Manipulator zwraca obiekt, który po wyodrębnieniu `str`ze strumienia `formatted input function` zachowuje się `get` jako funkcja elementu `money_get` członkowskiego `str`dla aspektu ustawień regionalnych skojarzonego z , używając *use_intl* do wskazania formatu międzynarodowego. Jeśli powiedzie się, wywołanie przechowuje w *ilości* wyodrębnionewarte pieniężne. Następnie manipulator `str`zwraca plik .

`Money`musi być `long double` typu lub wystąpienia `basic_string` z tego samego elementu i `str`parametrów cech, jak .

## <a name="get_time"></a><a name="iomanip_get_time"></a>get_time

Wyodrębnia wartość czasu ze strumienia przy użyciu żądanego formatu. Zwraca wartość w parametrze jako strukturę czasu.

```cpp
template <class Elem>
T10 put_time(struct tm *time_ptr, const Elem *time_format);
```

### <a name="parameters"></a>Parametry

*time_ptr*\
Czas w postaci struktury czasu.

*time_format*\
Żądany format do użycia w celu uzyskania wartości czasu.

### <a name="remarks"></a>Uwagi

Manipulator zwraca obiekt, który po wyodrębnieniu `str`ze strumienia `formatted input function` zachowuje się `get` jak funkcja elementu `time_get` członkowskiego `str`dla `tptr` aspektu ustawień regionalnych skojarzonego z , używając wskazania struktury czasu i `fmt` wskazania początku ciągu formatu zakończonego z wartością null. Jeśli powiedzie się, wywołanie przechowuje w strukturze czasu wartości skojarzone z wyodrębnionych pól czasu. Następnie manipulator `str`zwraca plik .

## <a name="put_money"></a><a name="iomanip_put_money"></a>put_money

Wstawia kwotę pieniężną przy użyciu żądanego formatu do strumienia.

```cpp
template <class Money>
T8 put_money(const Money& amount, bool use_intl);
```

### <a name="parameters"></a>Parametry

*Kwota*\
Kwota pieniężna do wstawienia do strumienia.

*use_intl*\
Ustaw **na true,** jeśli manipulator powinien używać formatu międzynarodowego, **false,** jeśli nie powinien.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `str`.

### <a name="remarks"></a>Uwagi

Manipulator zwraca obiekt, który po wstawieniu do `str`strumienia zachowuje się jako `put` sformatowana `money_put` funkcja wyjściowa, która wywołuje funkcję elementu członkowskiego dla aspektu ustawień regionalnych skojarzonego z programem `str`. Jeśli połączenie się powiedzie, zostanie wstawione `amount` odpowiednio sformatowane, używając *use_intl* do wskazania formatu międzynarodowego i `str.fill()`elementu wypełnienia. Następnie manipulator `str`zwraca plik .

`Money`musi być `long double` typu lub wystąpienia `basic_string` z tego samego elementu i `str`parametrów cech, jak .

## <a name="put_time"></a><a name="iomanip_put_time"></a>put_time

Zapisuje wartość czasu ze struktury czasu do strumienia przy użyciu określonego formatu.

```cpp
template <class Elem>
T10 put_time(struct tm* time_ptr, const Elem* time_format);
```

### <a name="parameters"></a>Parametry

*time_ptr*\
Wartość czasu do zapisu do strumienia, pod warunkiem w strukturze czasu.

*time_format*\
Żądany format do zapisania wartości czasu.

### <a name="remarks"></a>Uwagi

Manipulator zwraca obiekt, który po wstawieniu do `str` `formatted output function`strumienia zachowuje się jak . Funkcja wyjściowa wywołuje `put` funkcję elementu członkowskiego `time_put` dla `str`aspektu ustawień regionalnych skojarzonego z programem . Funkcja wyjściowa używa *time_ptr* do wskazania struktury czasu i *time_format,* aby wskazać początek ciągu formatu zakończonego z wartością null. Jeśli połączenie się powiedzie, wywołanie wstawia tekst dosłowny z ciągu formatu i przekonwertowane wartości ze struktury czasu. Następnie manipulator `str`zwraca plik .

## <a name="quoted"></a><a name="quoted"></a>Cytowany

**(Nowość w C++14)** Manipulator iostream, który umożliwia wygodne zaokrąglanie ciągów do i z strumieni przy użyciu operatorów >> i << .

```cpp
quoted(std::string str) // or wstring
quoted(const char* str) //or wchar_t*
quoted(std::string str, char delimiter, char escape) // or wide versions
quoted(const char* str, char delimiter, char escape) // or wide versions
```

### <a name="parameters"></a>Parametry

*Str*\
A std::string,\*char, string literal or raw string literal, or a wide version of any of these\*(np. std::wstring, wchar_t ).

*Ogranicznik*\
Znak określony przez użytkownika lub szeroki znak, który ma być używany jako ogranicznik na początku i na końcu ciągu.

*Uciec*\
Znak określony przez użytkownika lub szeroki znak, który ma być używany jako znak ucieczki dla sekwencji uszkowania w ciągu.

### <a name="remarks"></a>Uwagi

Zobacz [Korzystanie z operatorów wstawiania i formatu sterowania](../standard-library/using-insertion-operators-and-controlling-format.md).

### <a name="example"></a>Przykład

W tym przykładzie `quoted` pokazano, jak używać z domyślnym ogranicznikiem i znakiem ucieczki przy użyciu wąskich ciągów. Szerokie ciągi są jednakowo obsługiwane.

```cpp
#include <iostream>
#include <iomanip>
#include <sstream>

using namespace std;

void show_quoted_v_nonquoted()
{
    // Results are identical regardless of input string type:
    // string inserted { R"(This is a "sentence".)" }; // raw string literal
    // string inserted { "This is a \"sentence\"." };  // regular string literal
    const char* inserted = "This is a \"sentence\".";  // const char*
    stringstream ss, ss_quoted;
    string extracted, extracted_quoted;

    ss << inserted;
    ss_quoted << quoted(inserted);

    cout << "ss.str() is storing       : " << ss.str() << endl;
    cout << "ss_quoted.str() is storing: " << ss_quoted.str() << endl << endl;

    // Round-trip the strings
    ss >> extracted;
    ss_quoted >> quoted(extracted_quoted);

    cout << "After round trip: " << endl;
    cout << "Non-quoted      : " << extracted << endl;
    cout << "Quoted          : " << extracted_quoted << endl;
}

int main(int argc, char* argv[])
{
    show_quoted_v_nonquoted();

    // Keep console window open in debug mode.
    cout << endl << "Press Enter to exit" << endl;
    string input{};
    getline(cin, input);
}

/* Output:
ss.str() is storing       : This is a "sentence".
ss_quoted.str() is storing: "This is a \"sentence\"."

After round trip:
Non-quoted      : This
Quoted          : This is a "sentence".

Press Enter to exit
*/
```

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak podać niestandardowy znak ogranicznika i/lub znak ucieczki:

```cpp
#include <iostream>
#include <iomanip>
#include <sstream>

using namespace std;

void show_custom_delimiter()
{
    string inserted{ R"("This" "is" "a" "heavily-quoted" "sentence".)" };
    // string inserted{ "\"This\" \"is\" \"a\" \"heavily-quoted\" \"sentence\"" };
    // const char* inserted{ "\"This\" \"is\" \"a\" \"heavily-quoted\" \"sentence\"" };
    stringstream ss, ss_quoted;
    string extracted;

    ss_quoted << quoted(inserted, '*');
    ss << inserted;
    cout << "ss_quoted.str() is storing: " << ss_quoted.str() << endl;
    cout << "ss.str() is storing       : " << ss.str() << endl << endl;

    // Use the same quoted arguments as on insertion.
    ss_quoted >> quoted(extracted, '*');

    cout << "After round trip: " << endl;
    cout << "Quoted          : " << extracted << endl;

    extracted = {};
    ss >> extracted;
    cout << "Non-quoted      : " << extracted << endl << endl;
}

void show_custom_escape()
{
    string inserted{ R"(\\root\trunk\branch\nest\egg\yolk)" };
    // string inserted{ "\\\\root\\trunk\\branch\\nest\\egg\\yolk" };
    stringstream ss, ss_quoted, ss_quoted_custom;
    string extracted;

    // Use '"' as delimiter and '~' as escape character.
    ss_quoted_custom << quoted(inserted, '"', '~');
    ss_quoted << quoted(inserted);
    ss << inserted;
    cout << "ss_quoted_custom.str(): " << ss_quoted_custom.str() << endl;
    cout << "ss_quoted.str()       : " << ss_quoted.str() << endl;
    cout << "ss.str()              : " << ss.str() << endl << endl;

    // No spaces in this string, so non-quoted behaves same as quoted
    // after round-tripping.
}

int main(int argc, char* argv[])
{
    cout << "Custom delimiter:" << endl;
    show_custom_delimiter();
    cout << "Custom escape character:" << endl;
    show_custom_escape();

    // Keep console window open in debug mode.
    cout << endl << "Press Enter to exit" << endl;
    string input{};
    getline(cin, input);
}
/* Output:
Custom delimiter:
ss_quoted.str() is storing: *"This" "is" "a" "heavily-quoted" "sentence".*
ss.str() is storing       : "This" "is" "a" "heavily-quoted" "sentence".

After round trip:
Quoted          : "This" "is" "a" "heavily-quoted" "sentence".
Non-quoted      : "This"

Custom escape character:
ss_quoted_custom.str(): "\\root\trunk\branch\nest\egg\yolk"
ss_quoted.str()       : "\\\\root\\trunk\\branch\\nest\\egg\\yolk"
ss.str()              : \\root\trunk\branch\nest\egg\yolk

Press Enter to exit
*/
```

## <a name="resetiosflags"></a><a name="resetiosflags"></a>resetiosflags

Czyści określone flagi.

```cpp
T1 resetiosflags(ios_base::fmtflags mask);
```

### <a name="parameters"></a>Parametry

*Maska*\
Flagi, aby wyczyścić.

### <a name="return-value"></a>Wartość zwracana

Manipulator zwraca obiekt, który po wyodrębnieniu lub wstawieniu do `str`strumienia wywołuje `str.` [setf](../standard-library/ios-base-class.md#setf)`(ios_base::`[fmtflags](../standard-library/ios-base-class.md#fmtflags)`, mask)`, a następnie zwraca `str`.

### <a name="example"></a>Przykład

Zobacz [setw](../standard-library/iomanip-functions.md#setw) na przykład `resetiosflags`za pomocą .

## <a name="setbase"></a><a name="setbase"></a>baza setbase

Ustaw podstawę dla liczby całkowitej.

```cpp
T3 setbase(int base);
```

### <a name="parameters"></a>Parametry

*Podstawowej*\
Podstawa liczbowa.

### <a name="return-value"></a>Wartość zwracana

Manipulator zwraca obiekt, który po wyodrębnieniu lub wstawieniu do strumienia `str`wywołuje `str.setf(mask,` [ios_base::basefield](../standard-library/ios-base-class.md#fmtflags)`)`, a następnie zwraca `str`. W `mask` tym miejscu określa się w następujący sposób:

- Jeśli *podstawa* wynosi 8, to `mask` jest `ios_base::` [paź](../standard-library/ios-functions.md#oct).

- Jeśli *podstawa* wynosi 10, `ios_base::`to maska to [dec](../standard-library/ios-functions.md#dec).

- Jeśli *podstawa* wynosi 16, to `mask` jest `ios_base::` [hex](../standard-library/ios-functions.md#hex).

- Jeśli *podstawowa* jest dowolną inną `ios_base::`wartością, maska to [fmtflags](../standard-library/ios-base-class.md#fmtflags)`(0)`.

### <a name="example"></a>Przykład

Zobacz [setw](../standard-library/iomanip-functions.md#setw) na przykład `setbase`za pomocą .

## <a name="setfill"></a><a name="setfill"></a>setfill (setfill)

Ustawia znak, który będzie używany do wypełniania spacji na ekranie w prawozaprawnym.

```cpp
template <class Elem>
T4 setfill(Elem Ch);
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, który będzie używany do wypełniania spacji na ekranie wyrównanym do prawej.

### <a name="return-value"></a>Wartość zwracana

Manipulator szablonu zwraca obiekt, który po wyodrębnieniu lub `str`wstawieniu do strumienia `str.`wywołuje [wypełnienie,](../standard-library/basic-ios-class.md#fill)`(Ch)`a następnie zwraca `str`. Typ `Elem` musi być taki sam jak typ `str`elementu dla strumienia .

### <a name="example"></a>Przykład

Zobacz [setw](../standard-library/iomanip-functions.md#setw) na przykład `setfill`za pomocą .

## <a name="setiosflags"></a><a name="setiosflags"></a>setiosflags

Ustawia określone flagi.

```cpp
T2 setiosflags(ios_base::fmtflags mask);
```

### <a name="parameters"></a>Parametry

*Maska*\
Flagi do ustawionego.

### <a name="return-value"></a>Wartość zwracana

Manipulator zwraca obiekt, który po wyodrębnieniu lub wstawieniu do `str`strumienia wywołuje `str.` [setf,](../standard-library/ios-base-class.md#setf)`(mask)`a następnie zwraca `str`.

### <a name="example"></a>Przykład

Zobacz [setw](../standard-library/iomanip-functions.md#setw) na przykład `setiosflags`za pomocą .

## <a name="setprecision"></a><a name="setprecision"></a>setprecision (setprecision)

Ustawia dokładność wartości zmiennoprzecinkowych.

```cpp
T5 setprecision(streamsize Prec);
```

### <a name="parameters"></a>Parametry

*Prec (prec)*\
Dokładność wartości zmiennoprzecinkowych.

### <a name="return-value"></a>Wartość zwracana

Manipulator zwraca obiekt, który po wyodrębnieniu lub wstawieniu do strumienia `str`wywołuje `str.` [precyzję,](../standard-library/ios-base-class.md#precision)`(Prec)`a następnie zwraca `str`.

### <a name="example"></a>Przykład

Zobacz [setw](../standard-library/iomanip-functions.md#setw) na przykład `setprecision`za pomocą .

## <a name="setw"></a><a name="setw"></a>Setw

Określa szerokość pola wyświetlania dla następnego elementu w strumieniu.

```cpp
T6 setw(streamsize Wide);
```

### <a name="parameters"></a>Parametry

*Szeroki*\
Szerokość pola wyświetlania.

### <a name="return-value"></a>Wartość zwracana

Manipulator zwraca obiekt, który po wyodrębnieniu lub wstawieniu do `str`strumienia wywołuje `str.` [szerokość,](../standard-library/ios-base-class.md#width)`(Wide)`a następnie zwraca `str`.

### <a name="remarks"></a>Uwagi

setw ustawia szerokość tylko dla następnego elementu w strumieniu i musi być wstawiony przed każdym elementem, którego szerokość chcesz określić.

### <a name="example"></a>Przykład

```cpp
// iomanip_setw.cpp
// compile with: /EHsc
// Defines the entry point for the console application.
//
// Sample use of the following manipulators:
//   resetiosflags
//   setiosflags
//   setbase
//   setfill
//   setprecision
//   setw

#include <iostream>
#include <iomanip>

using namespace std;

const double   d1 = 1.23456789;
const double   d2 = 12.3456789;
const double   d3 = 123.456789;
const double   d4 = 1234.56789;
const double   d5 = 12345.6789;
const long      l1 = 16;
const long      l2 = 256;
const long      l3 = 1024;
const long      l4 = 4096;
const long      l5 = 65536;
int         base = 10;

void DisplayDefault( )
{
   cout << endl << "default display" << endl;
   cout << "d1 = " << d1 << endl;
   cout << "d2 = " << d2 << endl;
   cout << "d3 = " << d3 << endl;
   cout << "d4 = " << d4 << endl;
   cout << "d5 = " << d5 << endl;
}

void DisplayWidth( int n )
{
   cout << endl << "fixed width display set to " << n << ".\n";
   cout << "d1 = " << setw(n) << d1 << endl;
   cout << "d2 = " << setw(n) << d2 << endl;
   cout << "d3 = " << setw(n) << d3 << endl;
   cout << "d4 = " << setw(n) << d4 << endl;
   cout << "d5 = " << setw(n) << d5 << endl;
}

void DisplayLongs( )
{
   cout << setbase(10);
   cout << endl << "setbase(" << base << ")" << endl;
   cout << setbase(base);
   cout << "l1 = " << l1 << endl;
   cout << "l2 = " << l2 << endl;
   cout << "l3 = " << l3 << endl;
   cout << "l4 = " << l4 << endl;
   cout << "l5 = " << l5 << endl;
}

int main( int argc, char* argv[] )
{
   DisplayDefault( );

   cout << endl << "setprecision(" << 3 << ")" << setprecision(3);
   DisplayDefault( );

   cout << endl << "setprecision(" << 12 << ")" << setprecision(12);
   DisplayDefault( );

   cout << setiosflags(ios_base::scientific);
   cout << endl << "setiosflags(" << ios_base::scientific << ")";
   DisplayDefault( );

   cout << resetiosflags(ios_base::scientific);
   cout << endl << "resetiosflags(" << ios_base::scientific << ")";
   DisplayDefault( );

   cout << endl << "setfill('" << 'S' << "')" << setfill('S');
   DisplayWidth(15);
   DisplayDefault( );

   cout << endl << "setfill('" << ' ' << "')" << setfill(' ');
   DisplayWidth(15);
   DisplayDefault( );

   cout << endl << "setprecision(" << 8 << ")" << setprecision(8);
   DisplayWidth(10);
   DisplayDefault( );

   base = 16;
   DisplayLongs( );

   base = 8;
   DisplayLongs( );

   base = 10;
   DisplayLongs( );

   return   0;
}
```

```Output

default display
d1 = 1.23457
d2 = 12.3457
d3 = 123.457
d4 = 1234.57
d5 = 12345.7

setprecision(3)
default display
d1 = 1.23
d2 = 12.3
d3 = 123
d4 = 1.23e+003
d5 = 1.23e+004

setprecision(12)
default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setiosflags(4096)
default display
d1 = 1.234567890000e+000
d2 = 1.234567890000e+001
d3 = 1.234567890000e+002
d4 = 1.234567890000e+003
d5 = 1.234567890000e+004

resetiosflags(4096)
default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setfill('S')
fixed width display set to 15.
d1 = SSSSS1.23456789
d2 = SSSSS12.3456789
d3 = SSSSS123.456789
d4 = SSSSS1234.56789
d5 = SSSSS12345.6789

default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setfill(' ')
fixed width display set to 15.
d1 =      1.23456789
d2 =      12.3456789
d3 =      123.456789
d4 =      1234.56789
d5 =      12345.6789

default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setprecision(8)
fixed width display set to 10.
d1 =  1.2345679
d2 =  12.345679
d3 =  123.45679
d4 =  1234.5679
d5 =  12345.679

default display
d1 = 1.2345679
d2 = 12.345679
d3 = 123.45679
d4 = 1234.5679
d5 = 12345.679

setbase(16)
l1 = 10
l2 = 100
l3 = 400
l4 = 1000
l5 = 10000

setbase(8)
l1 = 20
l2 = 400
l3 = 2000
l4 = 10000
l5 = 200000

setbase(10)
l1 = 16
l2 = 256
l3 = 1024
l4 = 4096
l5 = 65536
```

## <a name="see-also"></a>Zobacz też

[\<>iomanip](../standard-library/iomanip.md)

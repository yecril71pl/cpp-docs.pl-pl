---
title: basic_ios — Klasa
ms.date: 11/04/2016
f1_keywords:
- ios/std::basic_ios
- ios/std::basic_ios::char_type
- ios/std::basic_ios::int_type
- ios/std::basic_ios::off_type
- ios/std::basic_ios::pos_type
- ios/std::basic_ios::traits_type
- ios/std::basic_ios::bad
- ios/std::basic_ios::clear
- ios/std::basic_ios::copyfmt
- ios/std::basic_ios::eof
- ios/std::basic_ios::exceptions
- ios/std::basic_ios::fail
- ios/std::basic_ios::fill
- ios/std::basic_ios::good
- ios/std::basic_ios::imbue
- ios/std::basic_ios::init
- ios/std::basic_ios::move
- ios/std::basic_ios::narrow
- ios/std::basic_ios::rdbuf
- ios/std::basic_ios::rdstate
- ios/std::basic_ios::set_rdbuf
- ios/std::basic_ios::setstate
- ios/std::basic_ios::swap
- ios/std::basic_ios::tie
- ios/std::basic_ios::widen
- ios/std::basic_ios::explicit operator bool
helpviewer_keywords:
- std::basic_ios [C++]
- std::basic_ios [C++], char_type
- std::basic_ios [C++], int_type
- std::basic_ios [C++], off_type
- std::basic_ios [C++], pos_type
- std::basic_ios [C++], traits_type
- std::basic_ios [C++], bad
- std::basic_ios [C++], clear
- std::basic_ios [C++], copyfmt
- std::basic_ios [C++], eof
- std::basic_ios [C++], exceptions
- std::basic_ios [C++], fail
- std::basic_ios [C++], fill
- std::basic_ios [C++], good
- std::basic_ios [C++], imbue
- std::basic_ios [C++], init
- std::basic_ios [C++], move
- std::basic_ios [C++], narrow
- std::basic_ios [C++], rdbuf
- std::basic_ios [C++], rdstate
- std::basic_ios [C++], set_rdbuf
- std::basic_ios [C++], setstate
- std::basic_ios [C++], swap
- std::basic_ios [C++], tie
- std::basic_ios [C++], widen
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
ms.openlocfilehash: 614e26b2329edeec2cccb32c7ba18b23e9d5320d
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688436"
---
# <a name="basic_ios-class"></a>basic_ios — Klasa

Szablon klasy zawiera opis funkcji magazynu i elementów członkowskich wspólnych dla strumieni danych wejściowych (klasy template [basic_istream](../standard-library/basic-istream-class.md)) i strumieni wyjściowych (klasy template [basic_ostream](../standard-library/basic-ostream-class.md)), które są zależne od parametrów szablonu. (Klasa [ios_base](../standard-library/ios-base-class.md) opisuje, co jest typowe i nie zależy od parametrów szablonu). Obiekt klasy **basic_ios \<class elem, cechy klas >** pomaga kontrolować strumień z elementami typu `Elem`, których cechy znaków są określane przez `Traits` klasy.

## <a name="syntax"></a>Składnia

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>Parametry

*Elem* \
Typ.

*Cechy* \
Zmienna typu `char_traits`.

## <a name="remarks"></a>Uwagi

Obiekt klasy **basic_ios \<class elem, cechy klasy >** sklepy:

- Wskaźnik powiązania do obiektu typu [basic_istream](../standard-library/basic-istream-class.md)  **\<Elem, cechy >** .

- Wskaźnik buforu strumienia do obiektu typu [basic_streambuf](../standard-library/basic-streambuf-class.md)  **\<Elem, cechy >** .

- [Informacje o formatowaniu](../standard-library/ios-base-class.md).

- [Informacje o stanie strumienia](../standard-library/ios-base-class.md) w obiekcie podstawowym typu [ios_base](../standard-library/ios-base-class.md).

- Znak wypełnienia w obiekcie typu `char_type`.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_ios](#basic_ios)|Konstruuje klasę `basic_ios`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Synonim dla parametru szablonu `Elem`.|
|[int_type](#int_type)|Synonim dla `Traits::int_type`.|
|[off_type](#off_type)|Synonim dla `Traits::off_type`.|
|[pos_type](#pos_type)|Synonim dla `Traits::pos_type`.|
|[traits_type](#traits_type)|Synonim dla parametru szablonu `Traits`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[ściągaln](#bad)|Wskazuje utratę integralności buforu strumienia.|
|[Wyczyść](#clear)|Czyści wszystkie flagi błędów.|
|[copyfmt](#copyfmt)|Kopiuje flagi z jednego strumienia do innego.|
|[eof](#eof)|Wskazuje, czy osiągnięto koniec strumienia.|
|[wyłączenia](#exceptions)|Wskazuje, które wyjątki zostaną zgłoszone przez strumień.|
|[udało](#fail)|Wskazuje, że nie powiodło się wyodrębnienie prawidłowego pola ze strumienia.|
|[pełni](#fill)|Określa lub zwraca znak, który będzie używany, gdy tekst nie jest tak szeroki jak strumień.|
|[aukcj](#good)|Wskazuje, że strumień jest w dobrym stanie.|
|[imbue —](#imbue)|Zmienia ustawienia regionalne.|
|[init](#init)|Wywoływane przez konstruktory `basic_ios`.|
|[Przenieś](#move)|Przenosi wszystkie wartości, z wyjątkiem wskaźnika do buforu strumienia, z parametru do bieżącego obiektu.|
|[dokładniej](#narrow)|Znajduje odpowiednik znaku w danym `char_type`.|
|[rdbuf](#rdbuf)|Kieruje strumień do określonego buforu.|
|[rdstate](#rdstate)|Odczytuje stan bitów dla flag.|
|[set_rdbuf](#set_rdbuf)|Przypisuje bufor strumienia jako bufor odczytu dla tego obiektu strumienia.|
|[Metoda setstate](#setstate)|Ustawia dodatkowe flagi.|
|[wymiany](#swap)|Wymienia wartości w tym obiekcie `basic_ios` dla tych z innego obiektu `basic_ios`. Wskaźniki do buforów strumieni nie są wymieniane.|
|[równe](#tie)|Zapewnia, że jeden strumień jest przetwarzany przed innym strumieniem.|
|[szerzon](#widen)|Znajduje odpowiednik `char_type` danego znaku.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[jawny operator logiczny](#op_bool)|Zezwala na użycie obiektu `basic_ios` jako wartości **logicznej**. Automatyczna konwersja typów jest wyłączona, aby zapobiec typowym, niezamierzonym efektom ubocznym.|
|[void — operator](#op_void_star)|Wskazuje, czy strumień jest wciąż dobry.|
|[zakład!](#op_not)|Wskazuje, czy strumień nie jest uszkodzony.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ios >

**Przestrzeń nazw:** std

## <a name="bad"></a>basic_ios:: zły

Wskazuje utratę integralności buforu strumienia

```cpp
bool bad() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli `rdstate & badbit` jest różna od zera; w przeciwnym razie **false**.

Aby uzyskać więcej informacji na temat `badbit`, zobacz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Przykład

```cpp
// basic_ios_bad.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.bad( );
    cout << boolalpha;
    cout << b << endl;

    b = cout.good( );
    cout << b << endl;
}
```

## <a name="basic_ios"></a>basic_ios::basic_ios

Konstruuje klasę basic_ios.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>Parametry

\ *SB*
Bufor standardowy do przechowywania elementów wejściowych lub wyjściowych.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje obiekty składowe przez wywołanie [init](#init)(_ *SB*). Drugi (chroniony) Konstruktor pozostawia obiekty składowe niezainicjowane. Późniejsze wywołanie `init` musi zainicjować obiekt, zanim będzie można go bezpiecznie zniszczyć.

## <a name="char_type"></a>basic_ios::char_type

Synonim dla parametru szablonu `Elem`.

```cpp
typedef Elem char_type;
```

## <a name="clear"></a>basic_ios:: Clear

Czyści wszystkie flagi błędów.

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>Parametry

\ *stanu*
Obowiązkowe Flagi, które mają zostać ustawione po wyczyszczeniu wszystkich flag. Wartość domyślna to `goodbit`.

*odzyskanie* \
Obowiązkowe Określa, czy wyjątek powinien zostać wywołany. Wartość domyślna to **false** (nie powoduje ponownego zgłoszenia wyjątku).

### <a name="remarks"></a>Uwagi

Flagi są `goodbit`, `failbit`, `eofbit` i `badbit`. Testuj dla tych flag z [dobrymi](#good), [nieprawidłowymi](#bad) [znacznikami EOF](#eof)i [niepowodzeniem](#fail)

Funkcja członkowska zastępuje informacje o stanie przechowywanego strumienia:

`state` &#124; `(`[rdbuf](#rdbuf) ! = 0 **goodbit** : **badbit**)

Jeśli `state` **&** [wyjątkami](#exceptions) jest różna od zera, zgłaszany jest obiekt [błędu](../standard-library/ios-base-class.md#failure)klasy.

### <a name="example"></a>Przykład

Zobacz [rdstate](#rdstate) i [getline](../standard-library/string-functions.md#getline) , aby poznać przykłady przy użyciu `clear`.

## <a name="copyfmt"></a>basic_ios::copyfmt

Kopiuje flagi z jednego strumienia do innego.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>Parametry

*prawa* \
Strumień, którego flagi mają zostać skopiowane.

### <a name="return-value"></a>Wartość zwracana

Obiekt **dla strumienia, do** którego są kopiowane flagi.

### <a name="remarks"></a>Uwagi

Funkcja członkowska raportuje **wyczyszczenie**zdarzenia wywołania zwrotnego \_event. Następnie kopiuje od *prawej* do **\*this** znak wypełnienia, wskaźnik powiązania i informacje o formatowaniu. Przed zmianą maski wyjątku raport jest raportowany `copyfmt_event` zdarzenia wywołania zwrotnego. Jeśli po zakończeniu kopiowania **stan &** [wyjątkami](#exceptions) jest różna od zera, funkcja skutecznie wywołuje metodę [Clear](#clear) z argumentem [rdstate](#rdstate). Zwraca **\*this**.

### <a name="example"></a>Przykład

```cpp
// basic_ios_copyfmt.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream x( "test.txt" );
    int i = 10;

    x << showpos;
    cout << i << endl;
    cout.copyfmt( x );
    cout << i << endl;
}
```

## <a name="eof"></a>basic_ios:: EOF

Wskazuje, czy osiągnięto koniec strumienia.

```cpp
bool eof() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli osiągnięto koniec strumienia, w przeciwnym razie **zwraca wartość false** .

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca **wartość true** , jeśli [rdstate](#rdstate) `& eofbit` jest różna od zera. Aby uzyskać więcej informacji na temat `eofbit`, zobacz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Przykład

```cpp
// basic_ios_eof.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

int main( int argc, char* argv[] )
{
    fstream   fs;
    int n = 1;
    fs.open( "basic_ios_eof.txt" );   // an empty file
    cout << boolalpha
    cout << fs.eof() << endl;
    fs >> n;   // Read the char in the file
    cout << fs.eof() << endl;
}
```

## <a name="exceptions"></a>basic_ios:: Exceptions

Wskazuje, które wyjątki zostaną zgłoszone przez strumień.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>Parametry

*Newexcept* \
Flagi, które mają zgłosić wyjątek.

### <a name="return-value"></a>Wartość zwracana

Flagi, które są obecnie określone do zgłaszania wyjątku dla strumienia.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca przechowywaną maskę wyjątków. Druga funkcja członkowska przechowuje *_Except* w masce wyjątku i zwraca jego poprzednią wartość przechowywaną. Należy zauważyć, że przechowywanie nowej maski wyjątków może zgłosić wyjątek, podobnie jak wywołanie [Clear](#clear)( [rdstate](#rdstate) ).

### <a name="example"></a>Przykład

```cpp
// basic_ios_exceptions.cpp
// compile with: /EHsc /GR
#include <iostream>

int main( )
{
    using namespace std;

    cout << cout.exceptions( ) << endl;
    cout.exceptions( ios::eofbit );
    cout << cout.exceptions( ) << endl;
    try
    {
        cout.clear( ios::eofbit );   // Force eofbit on
    }
    catch ( exception &e )
    {
        cout.clear( );
        cout << "Caught the exception." << endl;
        cout << "Exception class: " << typeid(e).name()  << endl;
        cout << "Exception description: " << e.what() << endl;
    }
}
```

```Output
0
1
Caught the exception.
Exception class: class std::ios_base::failure
Exception description: ios_base::eofbit set
```

## <a name="fail"></a>basic_ios:: niepowodzenie

Wskazuje, że nie powiodło się wyodrębnienie prawidłowego pola ze strumienia.

```cpp
bool fail() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli [rdstate](#rdstate) `& (badbit|failbit)` ma wartość różną od zera, w przeciwnym razie **false**.

Aby uzyskać więcej informacji na temat `failbit`, zobacz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Przykład

```cpp
// basic_ios_fail.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.fail( );
    cout << boolalpha;
    cout << b << endl;
}
```

## <a name="fill"></a>basic_ios:: Fill

Określa lub zwraca znak, który będzie używany, gdy tekst nie jest tak szeroki jak strumień.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>Parametry

@No__t_1 *char*
Znak, który ma być znakiem wypełnienia.

### <a name="return-value"></a>Wartość zwracana

Bieżący znak wypełnienia.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca przechowywany znak wypełnienia. Druga funkcja członkowska przechowuje *znak w znaku wypełnienia* i zwraca jego poprzednią wartość przechowywaną.

### <a name="example"></a>Przykład

```cpp
// basic_ios_fill.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( )
{
    using namespace std;

    cout << setw( 5 ) << 'a' << endl;
    cout.fill( 'x' );
    cout << setw( 5 ) << 'a' << endl;
    cout << cout.fill( ) << endl;
}
```

```Output
a
xxxxa
x
```

## <a name="good"></a>basic_ios:: dobra

Wskazuje, że strumień jest w dobrym stanie.

```cpp
bool good() const;
```

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli [rdstate](#rdstate) `== goodbit` (bez flag stanu nie są ustawione), w przeciwnym razie, **Fałsz**.

Aby uzyskać więcej informacji na temat `goodbit`, zobacz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Przykład

Zobacz [basic_ios:: Bad](#bad) , aby zapoznać się z przykładem użycia `good`.

## <a name="imbue"></a>basic_ios:: imbue —

Zmienia ustawienia regionalne.

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>Parametry

@No__t_1. *Loc*
Ciąg ustawień regionalnych.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienia regionalne.

### <a name="remarks"></a>Uwagi

Jeśli [rdbuf](#rdbuf) nie jest wskaźnikiem typu null, funkcja elementu członkowskiego wywołuje

`rdbuf` -> [pubimbue](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)

W każdym przypadku zwraca [ios_base:: imbue —](../standard-library/ios-base-class.md#imbue)(_ *Loc*).

### <a name="example"></a>Przykład

```cpp
// basic_ios_imbue.cpp
// compile with: /EHsc
#include <iostream>
#include <locale>

int main( )
{
    using namespace std;

    cout.imbue( locale( "french_france" ) );
    double x = 1234567.123456;
    cout << x << endl;
}
```

## <a name="init"></a>basic_ios:: init

Wywoływane przez konstruktory basic_ios.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>Parametry

*_Sb* \
Bufor standardowy do przechowywania elementów wejściowych lub wyjściowych.

*_Isstd* \
Określa, czy jest to strumień standardowy.

### <a name="remarks"></a>Uwagi

Funkcja członkowska przechowuje wartości we wszystkich obiektach Członkowskich, dzięki czemu:

- [rdbuf](#rdbuf) zwraca *_Sb.*

- Funkcja [krawat](#tie) zwraca wskaźnik o wartości null.

- [rdstate](#rdstate) zwraca [goodbit](../standard-library/ios-base-class.md#iostate) , jeśli *_Sb* jest różna od zera; w przeciwnym razie zwraca [badbit](../standard-library/ios-base-class.md#iostate).

- [wyjątki](#exceptions) zwracają `goodbit`.

- [flagi](../standard-library/ios-base-class.md#flags) zwracają [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [gru](../standard-library/ios-base-class.md#fmtflags).

- [Szerokość](../standard-library/ios-base-class.md#width) zwraca wartość 0.

- [dokładność](../standard-library/ios-base-class.md#precision) zwraca 6.

- Funkcja [Fill](#fill) zwraca znak spacji.

- [getloc](../standard-library/ios-base-class.md#getloc) zwraca `locale::classic`.

- Funkcja [iword](../standard-library/ios-base-class.md#iword) zwraca wartość zero, a funkcja [pword](../standard-library/ios-base-class.md#pword) zwraca wskaźnik o wartości null dla wszystkich wartości argumentów.

## <a name="int_type"></a>basic_ios::int_type

Synonim dla `traits_type::int_type`.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="move"></a>basic_ios:: Move

Przenosi wszystkie wartości, z wyjątkiem wskaźnika do buforu strumienia, z parametru do bieżącego obiektu.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

*prawa* \
Obiekt `ios_base`, z którego mają zostać przeniesione wartości.

### <a name="remarks"></a>Uwagi

Funkcja chroniona składowa przenosi wszystkie wartości przechowywane w *prawo* do `*this` z wyjątkiem przechowywanych `stream buffer pointer`, które nie zmieniły się w *prawo* i ustawiają wskaźnik null w `*this`. @No__t_0 przechowywanych jest ustawiona na pusty wskaźnik *po prawej stronie*.

## <a name="narrow"></a>basic_ios:: Narrow

Znajduje odpowiednik znaku w danym `char_type`.

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>Parametry

@No__t_1 *char*
**Znak** do przekonwertowania.

@No__t_1 *domyślne*
**Znak** , który ma zostać zwrócony, jeśli nie zostanie znaleziony odpowiednika.

### <a name="return-value"></a>Wartość zwracana

Odpowiednik **znaku** dla danego `char_type`.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [use_facet](../standard-library/basic-filebuf-class.md#open) \<ctype \<E > > ( [getloc](../standard-library/ios-base-class.md#getloc)()). `narrow` (`Char`, `Default`).

### <a name="example"></a>Przykład

```cpp
// basic_ios_narrow.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    wchar_t *x = L"test";
    char y[10];
    cout << x[0] << endl;
    wcout << x << endl;
    y[0] = wcout.narrow( x[0] );
    cout << y[0] << endl;
}
```

## <a name="off_type"></a>basic_ios::off_type

Synonim dla `traits_type::off_type`.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_void_star"></a>basic_ios:: operator void *

Wskazuje, czy strumień jest wciąż dobry.

```cpp
operator void *() const;
```

### <a name="return-value"></a>Wartość zwracana

Operator zwraca wskaźnik o wartości null tylko w przypadku [niepowodzenia](#fail).

### <a name="example"></a>Przykład

```cpp
// basic_ios_opgood.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << (bool)(&cout != 0) << endl;   // Stream is still good
}
```

```Output
1
```

## <a name="op_not"></a>basic_ios:: operator!

Wskazuje, czy strumień nie jest uszkodzony.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca [Niepowodzenie](#fail).

### <a name="example"></a>Przykład

```cpp
// basic_ios_opbad.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << !cout << endl;   // Stream is not bad
}
```

```Output
0
```

## <a name="op_bool"></a>basic_ios:: operator — bool

Zezwala na użycie obiektu `basic_ios` jako wartości **logicznej**. Automatyczna konwersja typów jest wyłączona, aby zapobiec typowym, niezamierzonym efektom ubocznym.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Uwagi

Operator zwraca wartość, która jest możliwa do przekonwertowania na **false** tylko wtedy, gdy `fail()`. Typ zwracany jest konwertowany tylko na **bool**, nie do `void *` ani do innego znanego typu skalarnego.

## <a name="pos_type"></a>basic_ios::p os_type

Synonim dla `traits_type::pos_type`.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="rdbuf"></a>basic_ios:: rdbuf

Kieruje strumień do określonego buforu.

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>Parametry

*_Sb* \
Strumień.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca wskaźnik przechowywanego buforu strumienia.

Druga funkcja członkowska przechowuje *_Sb* w wskaźniku buforu przechowywanego strumienia i zwraca poprzednio przechowywaną wartość.

### <a name="example"></a>Przykład

```cpp
// basic_ios_rdbuf.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream file( "rdbuf.txt" );
    streambuf *x = cout.rdbuf( file.rdbuf( ) );
    cout << "test" << endl;   // Goes to file
    cout.rdbuf(x);
    cout << "test2" << endl;
}
```

```Output
test2
```

## <a name="rdstate"></a>basic_ios::rdstate

Odczytuje stan bitów dla flag.

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>Wartość zwracana

Informacje o stanie przechowywanego strumienia.

### <a name="example"></a>Przykład

```cpp
// basic_ios_rdstate.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>
using namespace std;

void TestFlags( ios& x )
{
    cout << ( x.rdstate( ) & ios::badbit ) << endl;
    cout << ( x.rdstate( ) & ios::failbit ) << endl;
    cout << ( x.rdstate( ) & ios::eofbit ) << endl;
    cout << endl;
}

int main( )
{
    fstream x( "c:\test.txt", ios::out );
    x.clear( );
    TestFlags( x );
    x.clear( ios::badbit | ios::failbit | ios::eofbit );
    TestFlags( x );
}
```

```Output
0
0
0

4
2
1
```

## <a name="setstate"></a>basic_ios:: setstate

Ustawia dodatkowe flagi.

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>Parametry

*_State* \
Dodatkowe flagi do ustawienia.

### <a name="remarks"></a>Uwagi

Funkcja członkowska skutecznie wywołuje metodę [Clear](#clear)(_ *State* &#124; [rdstate](#rdstate)).

### <a name="example"></a>Przykład

```cpp
// basic_ios_setstate.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
using namespace std;

int main( )
{
    bool b = cout.bad( );
    cout << b << endl;   // Good
    cout.clear( ios::badbit );
    b = cout.bad( );
    // cout.clear( );
    cout << b << endl;   // Is bad, good
    b = cout.fail( );
    cout << b << endl;   // Not failed
    cout.setstate( ios::failbit );
    b = cout.fail( );
    cout.clear( );
    cout << b << endl;   // Is failed, good
    return 0;
}
```

```Output
0
1
```

## <a name="set_rdbuf"></a>basic_ios::set_rdbuf

Przypisuje bufor strumienia jako bufor odczytu dla tego obiektu strumienia.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>Parametry

*strbuf* \
Bufor strumienia, który ma zostać buforem odczytu.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego przechowuje *strbuf* w `stream buffer pointer`. nie wywołuje `clear`.

## <a name="tie"></a>basic_ios:: krawat

Zapewnia, że jeden strumień jest przetwarzany przed innym strumieniem.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>Parametry

*str* \
Strumień.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja członkowska zwraca przechowywany wskaźnik równości. Druga funkcja członkowska przechowuje *str* w wskaźniku krawat i zwraca jego poprzednią wartość przechowywaną.

### <a name="remarks"></a>Uwagi

`tie` powoduje, że dwa strumienie są synchronizowane, w tym, że operacje na jednym strumieniu występują po zakończeniu operacji w innym strumieniu.

### <a name="example"></a>Przykład

W tym przykładzie za pośrednictwem CIN do cout, jest gwarantowane, że ciąg "Wprowadź numer:" zostanie przeszedł do konsoli przed wyodrębnieniem samej liczby z CIN. Eliminuje to możliwość, że ciąg "Wprowadź numer:" nadal znajduje się w buforze, gdy numer jest odczytywany, dzięki czemu mamy pewność, że użytkownik ma pewien monit o odpowiedź. Domyślnie CIN i cout są powiązane.

```cpp
#include <ios>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    cin.tie( &cout );
    cout << "Enter a number:";
    cin >> i;
}
```

## <a name="traits_type"></a>basic_ios::traits_type

Synonim dla parametru szablonu `Traits`.

```cpp
typedef Traits traits_type;
```

## <a name="widen"></a>basic_ios:: rozszerzając

Znajduje odpowiednik `char_type` danego **znaku**.

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>Parametry

@No__t_1 *char*
Znak do przekonwertowania.

### <a name="return-value"></a>Wartość zwracana

Znajduje odpowiednik `char_type` danego **znaku**.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [use_facet](../standard-library/basic-filebuf-class.md#open) < **ctype** \< **E**> > ( [getloc](../standard-library/ios-base-class.md#getloc)). `widen` (`Char`).

### <a name="example"></a>Przykład

```cpp
// basic_ios_widen.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    char *z = "Hello";
    wchar_t y[2] = {0,0};
    cout << z[0] << endl;
    y[0] = wcout.widen( z[0] );
    wcout << &y[0] << endl;
}
```

## <a name="swap"></a>basic_ios:: swap

Wymienia wartości w tym obiekcie `basic_ios` dla tych z innego obiektu `basic_ios`. Jednak wskaźniki do buforów strumieni nie są wymieniane.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

*prawa* \
Obiekt `basic_ios`, który jest używany do wymiany wartości.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego wymienia wszystkie wartości przechowywane z *prawami* `*this` z wyjątkiem przechowywanych `stream buffer pointer`.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
\ [programowania iostream](../standard-library/iostream-programming.md)
[Konwencje iostream](../standard-library/iostreams-conventions.md)

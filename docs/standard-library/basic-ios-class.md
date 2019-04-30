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
ms.openlocfilehash: c22e048d01665deed83a9474525f414dfd874fe0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400659"
---
# <a name="basicios-class"></a>basic_ios — Klasa

Klasa szablonu Opisuje funkcje magazynu i elementów członkowskich, które muszą być wspólne dla obu strumienie wejściowe (szablonu klasy [basic_istream](../standard-library/basic-istream-class.md)) i strumieni danych wyjściowych (szablonu klasy [basic_ostream](../standard-library/basic-ostream-class.md)) zależą od Parametry szablonu. (Klasy [ios_base —](../standard-library/ios-base-class.md) w tym artykule opisano, co to jest typowe i nie jest zależny od parametrów szablonu.) Obiekt klasy **basic_ios —\<Elem klasy, klasy cech >** ułatwia kontrolowanie strumieni elementami typu `Elem`, którego cech są określane przez klasę `Traits`.

## <a name="syntax"></a>Składnia

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Typ.

*Cechy*<br/>
Zmienna typu `char_traits`.

## <a name="remarks"></a>Uwagi

Obiekt klasy **basic_ios —\<Elem klasy, klasy cech >** przechowuje:

- Tie wskaźnik do obiektu typu [basic_istream](../standard-library/basic-istream-class.md)**\<Elem, cechy >**.

- Wskaźnik buforu strumienia na obiekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, cechy >**.

- [Informacje o formatowaniu](../standard-library/ios-base-class.md).

- [Informacje o stanie Stream](../standard-library/ios-base-class.md) w obiektu podstawowego typu [ios_base —](../standard-library/ios-base-class.md).

- Znak wypełnienia w obiekt typu `char_type`.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_ios](#basic_ios)|Konstruuje `basic_ios` klasy.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Synonim dla parametru szablonu `Elem`.|
|[int_type](#int_type)|Synonim dla `Traits::int_type`.|
|[off_type](#off_type)|Synonim dla `Traits::off_type`.|
|[pos_type](#pos_type)|Synonim dla `Traits::pos_type`.|
|[traits_type](#traits_type)|Synonim dla parametru szablonu `Traits`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[bad](#bad)|Wskazuje utraty integralności buforu strumienia.|
|[Usuń zaznaczenie](#clear)|Czyści wszystkie flagi błędu.|
|[copyfmt](#copyfmt)|Kopiuje flagi z jednym strumień.|
|[eof](#eof)|Wskazuje, jeśli osiągnięto koniec strumienia.|
|[Wyjątki](#exceptions)|Wskazuje, której wyjątki zostaną zgłoszone przez strumień.|
|[Niepowodzenie](#fail)|Wskazuje błąd, aby wyodrębnić prawidłowym polem ze strumienia.|
|[Wypełnienie](#fill)|Określa, czy zwraca znak, który będzie używany, gdy tekst nie jest szerokie, jak strumień.|
|[dobre](#good)|Wskazuje, że strumień jest w dobrym stanie.|
|[imbue](#imbue)|Zmiany ustawień regionalnych.|
|[init](#init)|Wywoływane przez `basic_ios` konstruktorów.|
|[Przenieś](#move)|Przenosi wszystkie wartości, z wyjątkiem wskaźnik do buforu strumienia z parametru, jak bieżący obiekt.|
|[Zawęź](#narrow)|Umożliwia znalezienie równoważne znaku do danego `char_type`.|
|[rdbuf](#rdbuf)|Strumień trasy do określonego bufora.|
|[rdstate](#rdstate)|Odczytuje stan usługi bits dla flag.|
|[set_rdbuf](#set_rdbuf)|Przydziela bufor strumienia do buforu odczytu dla tego obiektu strumienia.|
|[setstate](#setstate)|Ustawia dodatkowe flagi.|
|[swap](#swap)|Wymienia wartości w tym `basic_ios` obiektu dla osób z innej `basic_ios` obiektu. Wskaźników do buforów strumienia nie zostały zamienione.|
|[tie](#tie)|Gwarantuje, że ten jeden strumień jest przetwarzana przed innym strumienia.|
|[widen](#widen)|Znajduje odpowiednik `char_type` do danego znaku.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[bool operatora Explicit](#op_bool)|Umożliwia korzystanie z `basic_ios` obiektu jako **bool**. Konwersja typu automatyczne jest wyłączona, aby uniknąć typowych i niezamierzone efekty uboczne.|
|[operator void *](#op_void_star)|Wskazuje, czy strumień jest w dalszym ciągu idealnie sprawdzają.|
|[operator!](#op_not)|Wskazuje, jeżeli strumień jest nieodpowiedni.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<dla systemu ios >

**Namespace:** standardowe

## <a name="bad"></a>  basic_ios::bad

Wskazuje utraty integralności bufor strumienia

```cpp
bool bad() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `rdstate & badbit` jest różna od zera; w przeciwnym razie **false**.

Aby uzyskać więcej informacji na temat `badbit`, zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="basic_ios"></a>  basic_ios::basic_ios

Tworzy basic_ios — klasa.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>Parametry

*sb*<br/>
Standardowa bufor do przechowywania elementów wejściowych lub wyjściowych.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje jego obiektu elementu członkowskiego, wywołując [init](#init)(_ *Sb*). Drugi Konstruktor (chroniony) pozostawia członków niezainicjowane obiekty. Nowsze wywołanie `init` należy zainicjować obiektu, zanim może zostać bezpiecznie zniszczone.

## <a name="char_type"></a>  basic_ios::char_type

Synonim dla parametru szablonu `Elem`.

```cpp
typedef Elem char_type;
```

## <a name="clear"></a>  basic_ios::Clear

Czyści wszystkie flagi błędu.

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>Parametry

*state*<br/>
(Opcjonalnie) Flagi, które chcesz ustawić po wyczyszczeniu wszystkie flagi. Wartość domyślna to `goodbit`.

*reraise —*<br/>
(Opcjonalnie) Określa, czy wyjątek powinien być ponownie podniesiona podstawa. Wartość domyślna to **false** (nie ponownie zgłosi wyjątek).

### <a name="remarks"></a>Uwagi

Flagi są `goodbit`, `failbit`, `eofbit`, i `badbit`. Test dla tych flag z [dobre](#good), [zły](#bad), [eof](#eof), i [zakończyć się niepowodzeniem](#fail)

Funkcji składowej zastępuje informacje o stanie przechowywanych strumienia za pomocą:

`state` &#124;`(` [rdbuf —](#rdbuf) ! = 0 **goodbit** : **badbit**)

Jeśli `state` **&** [wyjątki](#exceptions) jest różna od zera, następnie wyrzuca obiekt klasy [błąd](../standard-library/ios-base-class.md#failure).

### <a name="example"></a>Przykład

Zobacz [rdstate —](#rdstate) i [getline —](../standard-library/string-functions.md#getline) przykłady użycia `clear`.

## <a name="copyfmt"></a>  basic_ios::copyfmt

Kopiuje flagi z jednym strumień.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Strumień, którego flagi, które chcesz skopiować.

### <a name="return-value"></a>Wartość zwracana

**To** obiektu strumienia, do którego kopiowane są flagi.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zgłasza zdarzenie wywołania zwrotnego **wymazać\_zdarzeń**. Następnie kopiuje z *prawo* do  **\*to** znak wypełnienia wskaźnika tie oraz informacje o formatowaniu. Przed zmianą maski wyjątków, zgłasza zdarzenie wywołania zwrotnego `copyfmt_event`. Jeśli po zakończeniu kopiowania **stan &**[wyjątki](#exceptions) jest różna od zera, funkcja wywołuje [wyczyść](#clear) z argumentem [rdstate —](#rdstate). Zwraca  **\*to**.

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

## <a name="eof"></a>  basic_ios::EOF

Wskazuje, jeśli osiągnięto koniec strumienia.

```cpp
bool eof() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** jeśli osiągnięto koniec strumienia, **false** inaczej.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca **true** Jeśli [rdstate —](#rdstate) `& eofbit` jest różna od zera. Aby uzyskać więcej informacji na temat `eofbit`, zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="exceptions"></a>  basic_ios::Exceptions

Wskazuje, której wyjątki zostaną zgłoszone przez strumień.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>Parametry

*Newexcept*<br/>
Flagi, które mają zostać zgłoszony wyjątek.

### <a name="return-value"></a>Wartość zwracana

Flagi, które są aktualnie określone do zgłoszony wyjątek dla strumienia.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca maski wyjątku przechowywanych. Drugi magazynów funkcja elementu członkowskiego *_Except* maskę wyjątku i zwraca jego poprzedniej przechowywaną wartość. Należy pamiętać, że przechowywanie nową maskę wyjątku może zgłosić wyjątek podobnie jak wywołanie [wyczyść](#clear)( [rdstate —](#rdstate) ).

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

## <a name="fail"></a>  basic_ios::fail

Wskazuje błąd, aby wyodrębnić prawidłowym polem ze strumienia.

```cpp
bool fail() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli [rdstate —](#rdstate) `& (badbit|failbit)` jest różna od zera, w przeciwnym razie **false**.

Aby uzyskać więcej informacji na temat `failbit`, zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="fill"></a>  basic_ios::Fill

Określa, czy zwraca znak, który będzie używany, gdy tekst nie jest szerokie, jak strumień.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>Parametry

*Char*<br/>
Znak, który ma być znak wypełnienia.

### <a name="return-value"></a>Wartość zwracana

Bieżący znak wypełnienia.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca znak odpowiadający przechowywanej wypełnienia. Drugi magazynów funkcja elementu członkowskiego *Char* wypełnienia znaku i zwraca jego poprzedniej przechowywaną wartość.

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

## <a name="good"></a>  basic_ios::Good

Wskazuje, że strumień jest w dobrym stanie.

```cpp
bool good() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli [rdstate —](#rdstate) `== goodbit` (nie flagi stanu są ustawione), w przeciwnym razie **false**.

Aby uzyskać więcej informacji na temat `goodbit`, zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Przykład

Zobacz [basic_ios::bad](#bad) na przykład za pomocą `good`.

## <a name="imbue"></a>  basic_ios::imbue

Zmiany ustawień regionalnych.

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Lokalizacja*<br/>
Ciąg ustawień regionalnych.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienia regionalne.

### <a name="remarks"></a>Uwagi

Jeśli [rdbuf —](#rdbuf) jest nie wskaźnikiem typu null, element członkowski wywołania funkcji

`rdbuf`-> [pubimbue —](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)

W każdym przypadku zwraca [ios_base::imbue](../standard-library/ios-base-class.md#imbue)(_ *Loc*).

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

## <a name="init"></a>  basic_ios::init

Metoda wywoływana przez konstruktory basic_ios —.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>Parametry

*_Sb*<br/>
Standardowa bufor do przechowywania elementów wejściowych lub wyjściowych.

*_Isstd*<br/>
Określa, czy jest to Standardowy strumień.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zapisuje wartości we wszystkich obiektach elementu członkowskiego, tak aby:

- [rdbuf —](#rdbuf) zwraca *_Sb.*

- [Powiązanie](#tie) zwraca wskaźnik o wartości null.

- [rdstate —](#rdstate) zwraca [goodbit](../standard-library/ios-base-class.md#iostate) Jeśli *_Sb* jest różna od zera; w przeciwnym razie zwraca [badbit](../standard-library/ios-base-class.md#iostate).

- [Wyjątki](#exceptions) zwraca `goodbit`.

- [flagi](../standard-library/ios-base-class.md#flags) zwraca [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [gru](../standard-library/ios-base-class.md#fmtflags).

- [szerokość](../standard-library/ios-base-class.md#width) zwraca wartość 0.

- [dokładność](../standard-library/ios-base-class.md#precision) zwróci wynik 6.

- [wypełnienie](#fill) zwraca znak spacji.

- [getloc —](../standard-library/ios-base-class.md#getloc) zwraca `locale::classic`.

- [iword —](../standard-library/ios-base-class.md#iword) zwraca zero, a [pword —](../standard-library/ios-base-class.md#pword) zwraca pusty wskaźnik dla wszystkich wartości argumentu.

## <a name="int_type"></a>  basic_ios::int_type

Synonim dla `traits_type::int_type`.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="move"></a>  basic_ios::MOVE

Przenosi wszystkie wartości, z wyjątkiem wskaźnik do buforu strumienia z parametru, jak bieżący obiekt.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
`ios_base` Przesunięcia wartości z.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego chronionego przenosi wszystkie wartości, które są przechowywane w *prawo* do `*this` , z wyjątkiem przechowywanych `stream buffer pointer`, który nie jest zmienione *prawo* a wskaźnikiem typu null w `*this`. Przechowywany `tie pointer` jest ustawiona na wartość null wskaźnika w *prawo*.

## <a name="narrow"></a>  basic_ios::Narrow

Umożliwia znalezienie równoważne znaku do danego `char_type`.

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>Parametry

*Char*<br/>
**Char** do przekonwertowania.

*Default*<br/>
**Char** czy mają być zwracane, jeśli znaleziono odpowiednika.

### <a name="return-value"></a>Wartość zwracana

Odpowiednik **char** do danego `char_type`.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [use_facet](../standard-library/basic-filebuf-class.md#open)\<ctype\<E >> ( [getloc —](../standard-library/ios-base-class.md#getloc)()).`narrow` ( `Char`, `Default`).

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

## <a name="off_type"></a>  basic_ios::off_type

Synonim dla `traits_type::off_type`.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_void_star"></a>  basic_ios::operator void *

Wskazuje, czy strumień jest w dalszym ciągu idealnie sprawdzają.

```cpp
operator void *() const;
```

### <a name="return-value"></a>Wartość zwracana

Operator zwraca wskaźnika o wartości null tylko wtedy, gdy [się nie powieść](#fail).

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

## <a name="op_not"></a>  basic_ios::operator!

Wskazuje, jeżeli strumień jest nieodpowiedni.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca [się nie powieść](#fail).

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

## <a name="op_bool"></a>  basic_ios::operator bool

Umożliwia korzystanie z `basic_ios` obiektu jako **bool**. Konwersja typu automatyczne jest wyłączona, aby uniknąć typowych i niezamierzone efekty uboczne.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Uwagi

Operator zwraca można przekonwertować wartości na **false** tylko wtedy, gdy `fail()`. Typ zwracany jest konwertowany tylko **bool**, nie `void *` lub innych znanych typów skalarnych.

## <a name="pos_type"></a>  basic_ios::pos_type

Synonim dla `traits_type::pos_type`.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="rdbuf"></a>  basic_ios::rdbuf

Strumień trasy do określonego bufora.

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>Parametry

*_Sb*<br/>
Strumień.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca wskaźnik buforu strumienia przechowywanych.

Drugi magazynów funkcja elementu członkowskiego *_Sb* we wskaźniku buforu strumienia przechowywanych i zwraca wartość zapisanych wcześniej.

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

## <a name="rdstate"></a>  basic_ios::rdstate

Odczytuje stan usługi bits dla flag.

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>Wartość zwracana

Informacje o stanie przechowywanych strumienia.

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

## <a name="setstate"></a>  basic_ios::setstate

Ustawia dodatkowe flagi.

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>Parametry

*_Stanu*<br/>
Dodatkowe flagi, aby ustawić.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego skutecznie wywołuje [wyczyść](#clear)(_ *stanu* &#124; [rdstate —](#rdstate)).

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

## <a name="set_rdbuf"></a>  basic_ios::set_rdbuf

Przydziela bufor strumienia do buforu odczytu dla tego obiektu strumienia.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>Parametry

*strbuf*<br/>
Bufor strumienia przestanie buforu odczytu.

### <a name="remarks"></a>Uwagi

Chroniony element członkowski funkcji magazynów *strbuf* w `stream buffer pointer`. Nie wywołuje `clear`.

## <a name="tie"></a>  basic_ios::tie

Gwarantuje, że ten jeden strumień jest przetwarzana przed innym strumienia.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Strumień.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca wskaźnik tie przechowywanych. Drugi magazynów funkcja elementu członkowskiego *str* tie wskaźnika i zwraca jego poprzedniej przechowywaną wartość.

### <a name="remarks"></a>Uwagi

`tie` powoduje dwóch strumieni, które mają być synchronizowane w taki sposób, że operacje na jeden strumień wystąpić po zakończeniu operacji w usłudze stream.

### <a name="example"></a>Przykład

W tym przykładzie przez wiązanie cin do cout, ma żadnej gwarancji, że "Wprowadź liczbę:" ciąg zostanie umieszczona w konsoli przed numerem, sama są wyodrębniane z cin. Pozwala to wyeliminować możliwość który "Wprowadź liczbę:" ciągu nadal znajdują się w buforze, jeśli liczba jest odczytu, tak, aby się upewnić, że użytkownika faktycznie niektóre wiersz, aby odpowiedzieć na. Domyślnie cin i cout są powiązane.

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

## <a name="traits_type"></a>  basic_ios::traits_type

Synonim dla parametru szablonu `Traits`.

```cpp
typedef Traits traits_type;
```

## <a name="widen"></a>  basic_ios::widen

Znajduje odpowiednik `char_type` do danego **char**.

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>Parametry

*Char*<br/>
Znak, który ma zostać przekształcony.

### <a name="return-value"></a>Wartość zwracana

Znajduje odpowiednik `char_type` do danego **char**.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **E**>> ( [getloc —](../standard-library/ios-base-class.md#getloc)). `widen`( `Char`).

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

## <a name="swap"></a>  basic_ios::swap

Wymienia wartości w tym `basic_ios` obiektu dla osób z innej `basic_ios` obiektu. Jednakże wskaźniki do buforów strumienia nie zostały zamienione.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
`basic_ios` Obiekt, który jest używany do wymiany wartości.

### <a name="remarks"></a>Uwagi

Chroniona funkcja elementu członkowskiego wymienia wszystkie wartości, które są przechowywane w *prawo* z `*this` , z wyjątkiem przechowywanych `stream buffer pointer`.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>

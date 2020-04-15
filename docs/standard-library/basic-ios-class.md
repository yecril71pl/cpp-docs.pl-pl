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
ms.openlocfilehash: c8f883dd4f946c03aaa22dffcf5a3164a539d041
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364925"
---
# <a name="basic_ios-class"></a>basic_ios — Klasa

Szablon klasy opisuje funkcje magazynu i elementów członkowskich wspólne dla zarówno strumieni wejściowych (szablonu klasy [basic_istream)](../standard-library/basic-istream-class.md)i strumieni wyjściowych [(szablonu](../standard-library/basic-ostream-class.md)klasy basic_ostream ), które zależą od parametrów szablonu. (Klasa [ios_base](../standard-library/ios-base-class.md) opisuje, co jest wspólne i nie zależy od parametrów szablonu.) Obiekt klasy **basic_ios\<klasy Elem, class Cecha>** pomaga kontrolować strumień z elementami typu, `Elem`których cechy charakteru `Traits`są określane przez klasę .

## <a name="syntax"></a>Składnia

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ.

*Cechy*\
Zmienna typu `char_traits`.

## <a name="remarks"></a>Uwagi

Obiekt klasy **basic_ios\<klasy Elem, klasa Cechy>magazyny:**

- Wskaźnik wiązania do obiektu typu [basic_istream](../standard-library/basic-istream-class.md)**\<Elem, Cechy>**.

- Wskaźnik buforu strumienia do obiektu typu [basic_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, Cechy >**.

- [Informacje o formatowaniu](../standard-library/ios-base-class.md).

- [Przesyłaj strumieniowo informacje o stanie](../standard-library/ios-base-class.md) w obiekcie podstawowym typu [ios_base](../standard-library/ios-base-class.md).

- Znak wypełnienia w obiekcie `char_type`typu .

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_ios](#basic_ios)|Konstruuje `basic_ios` klasę.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Synonim parametru `Elem`szablonu .|
|[Int_type](#int_type)|Synonimem . `Traits::int_type`|
|[off_type](#off_type)|Synonimem . `Traits::off_type`|
|[pos_type](#pos_type)|Synonimem . `Traits::pos_type`|
|[traits_type](#traits_type)|Synonim parametru `Traits`szablonu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Bad](#bad)|Wskazuje utratę integralności buforu strumienia.|
|[Wyczyść](#clear)|Czyści wszystkie flagi błędów.|
|[copyfmt](#copyfmt)|Kopiuje flagi z jednego strumienia do drugiego.|
|[eof](#eof)|Wskazuje, czy osiągnięto koniec strumienia.|
|[Wyjątki](#exceptions)|Wskazuje, które wyjątki zostaną zrzucone przez strumień.|
|[Nie](#fail)|Wskazuje, że nie można wyodrębnić prawidłowego pola ze strumienia.|
|[fill](#fill)|Określa lub zwraca znak, który będzie używany, gdy tekst nie jest tak szeroki jak strumień.|
|[Dobry](#good)|Wskazuje, że strumień jest w dobrym stanie.|
|[Nasycić](#imbue)|Zmienia ustawienia regionalne.|
|[Init](#init)|Wywoływane `basic_ios` przez konstruktorów.|
|[Przenieść](#move)|Przenosi wszystkie wartości, z wyjątkiem wskaźnika do buforu strumienia, z parametru do bieżącego obiektu.|
|[Wąskie](#narrow)|Znajduje równoważny char `char_type`do danego .|
|[Rdbuf](#rdbuf)|Trasy strumienia do określonego buforu.|
|[rdstate](#rdstate)|Odczytuje stan bitów dla flag.|
|[set_rdbuf](#set_rdbuf)|Przypisuje bufor strumienia do buforu odczytu dla tego obiektu strumienia.|
|[stan zestawu](#setstate)|Ustawia dodatkowe flagi.|
|[Wymiany](#swap)|Wymienia wartości w `basic_ios` tym obiekcie `basic_ios` dla wartości innego obiektu. Wskaźniki do buforów strumienia nie są zamienione.|
|[Krawat](#tie)|Zapewnia, że jeden strumień jest przetwarzany przed innym strumieniem.|
|[Poszerzyć](#widen)|Znajduje odpowiednik `char_type` danego char.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[jawny bool operatora](#op_bool)|Umożliwia użycie `basic_ios` obiektu jako **bool**. Automatyczna konwersja typu jest wyłączona, aby zapobiec częstym, niezamierzonych skutków ubocznych.|
|[nieważne przez operatora *](#op_void_star)|Wskazuje, czy strumień jest nadal dobry.|
|[Operator!](#op_not)|Wskazuje, czy strumień nie jest zły.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ios>

**Przestrzeń nazw:** std

## <a name="basic_iosbad"></a><a name="bad"></a>basic_ios::zły

Wskazuje utratę integralności buforu strumienia

```cpp
bool bad() const;
```

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli `rdstate & badbit` jest niezerowa; w przeciwnym razie **false**.

Aby uzyskać `badbit`więcej informacji na temat , zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="basic_iosbasic_ios"></a><a name="basic_ios"></a>basic_ios::basic_ios

Konstruuje klasę basic_ios.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>Parametry

*Sb*\
Standardowy bufor do przechowywania elementów wejściowych lub wyjściowych.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje swoje obiekty członkowskie, wywołując [init](#init)(_ *Sb*). Drugi (chroniony) konstruktor pozostawia jego obiekty członkowskie niezainicjowane. Późniejsze wywołanie musi zainicjować `init` obiekt, zanim będzie można go bezpiecznie zniszczyć.

## <a name="basic_ioschar_type"></a><a name="char_type"></a>basic_ios::char_type

Synonim parametru `Elem`szablonu .

```cpp
typedef Elem char_type;
```

## <a name="basic_iosclear"></a><a name="clear"></a>basic_ios::wyczyść

Czyści wszystkie flagi błędów.

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>Parametry

*Państwa*\
(Opcjonalnie) Flagi, które chcesz ustawić po wyczyszczeniu wszystkich flag. Wartość domyślna to `goodbit`.

*ponowne przerasyć*\
(Opcjonalnie) Określa, czy wyjątek powinien zostać ponownie podniesiony. Domyślnie **false** (nie spowoduje ponownego podniesienia wyjątku).

### <a name="remarks"></a>Uwagi

Flagi są `goodbit` `failbit`, `eofbit`, `badbit`, i . Test dla tych flag z [dobrym,](#good) [złym](#bad), [eof](#eof), i [nie](#fail)

Funkcja elementu członkowskiego zastępuje przechowywane informacje o stanie strumienia:

`state``(`&#124; [rdbuf](#rdbuf) != 0 **goodbit** : **badbit**)

Jeśli `state` **&** [wyjątki niezerowe,](#exceptions) następnie zgłasza obiekt [błędu](../standard-library/ios-base-class.md#failure)klasy .

### <a name="example"></a>Przykład

Zobacz [rdstate](#rdstate) i [getline](../standard-library/string-functions.md#getline) `clear`przykłady za pomocą .

## <a name="basic_ioscopyfmt"></a><a name="copyfmt"></a>basic_ios::copyfmt

Kopiuje flagi z jednego strumienia do drugiego.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Strumień, którego flagi chcesz skopiować.

### <a name="return-value"></a>Wartość zwracana

**Ten** obiekt dla strumienia, do którego są kopiowanie flag.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zgłasza **zdarzenie wymazywania wywołania zwrotnego\_**. Następnie kopiuje z ** \*** *prawej* do tego znak wypełnienia, wskaźnik wiązania i informacje o formatowaniu. Przed zmianą maski wyjątku, zgłasza `copyfmt_event`zdarzenie wywołania zwrotnego . Jeśli po zakończeniu kopiowania **stan &** [wyjątków](#exceptions) jest niezerowy, funkcja skutecznie wywołuje [jasne](#clear) z argumentem [rdstate](#rdstate). Zwraca ** \*to**.

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

## <a name="basic_ioseof"></a><a name="eof"></a>basic_ios::eof

Wskazuje, czy osiągnięto koniec strumienia.

```cpp
bool eof() const;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli osiągnięto koniec strumienia, **false** inaczej.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca **wartość true,** jeśli [rdstate](#rdstate) `& eofbit` jest niezerowy. Aby uzyskać `eofbit`więcej informacji na temat , zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="basic_iosexceptions"></a><a name="exceptions"></a>basic_ios::wyjątki

Wskazuje, które wyjątki zostaną zrzucone przez strumień.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>Parametry

*Newexcept (wyeksja now*\
Flagi, które chcesz zgłosić wyjątek.

### <a name="return-value"></a>Wartość zwracana

Flagi, które są obecnie określone do zarzucenia wyjątku dla strumienia.

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu członkowskiego zwraca maskę wyjątku przechowywane. Funkcja drugiego elementu członkowskiego przechowuje *_Except* w masce wyjątków i zwraca jego poprzednią przechowywaną wartość. Należy zauważyć, że przechowywanie nowej maski wyjątku może zgłosić wyjątek, podobnie jak [wywołanie clear](#clear) [(rdstate).](#rdstate)

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

## <a name="basic_iosfail"></a><a name="fail"></a>basic_ios::fail

Wskazuje, że nie można wyodrębnić prawidłowego pola ze strumienia.

```cpp
bool fail() const;
```

### <a name="return-value"></a>Wartość zwracana

**true** if [rdstate](#rdstate) `& (badbit|failbit)` is nonzero, otherwise **false**.

Aby uzyskać `failbit`więcej informacji na temat , zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="basic_iosfill"></a><a name="fill"></a>basic_ios::wypełnienie

Określa lub zwraca znak, który będzie używany, gdy tekst nie jest tak szeroki jak strumień.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>Parametry

*Char*\
Znak, który ma być znakiem wypełnienia.

### <a name="return-value"></a>Wartość zwracana

Bieżący znak wypełnienia.

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu członkowskiego zwraca zapisany znak wypełnienia. Druga funkcja elementu członkowskiego przechowuje *Char* we znaku wypełnienia i zwraca jego poprzednią przechowywaną wartość.

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

## <a name="basic_iosgood"></a><a name="good"></a>basic_ios::dobry

Wskazuje, że strumień jest w dobrym stanie.

```cpp
bool good() const;
```

### <a name="return-value"></a>Wartość zwracana

**true** if [rdstate](#rdstate) `== goodbit` (nie są ustawione flagi państwowe), w przeciwnym razie **false**.

Aby uzyskać `goodbit`więcej informacji na temat , zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Przykład

Zobacz [basic_ios::bad](#bad) na przykład za `good`pomocą .

## <a name="basic_iosimbue"></a><a name="imbue"></a>basic_ios::imbue

Zmienia ustawienia regionalne.

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Ciąg ustawień regionalnych.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienia regionalne.

### <a name="remarks"></a>Uwagi

Jeśli [rdbuf](#rdbuf) nie jest wskaźnikiem zerowym, funkcja elementu członkowskiego wywołuje

`rdbuf`-> [pubimbue](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)

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

## <a name="basic_iosinit"></a><a name="init"></a>basic_ios::init

Wywoływana przez konstruktorów basic_ios.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>Parametry

*_Sb*\
Standardowy bufor do przechowywania elementów wejściowych lub wyjściowych.

*_Isstd*\
Określa, czy jest to strumień standardowy.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego przechowuje wartości we wszystkich obiektach członkowskich, dzięki czemu:

- [rdbuf](#rdbuf) zwraca *_Sb.*

- [zwraca](#tie) wskaźnik zerowy.

- [rdstate](#rdstate) zwraca [goodbit,](../standard-library/ios-base-class.md#iostate) jeśli *_Sb* jest niezerowy; w przeciwnym razie zwraca [badbit](../standard-library/ios-base-class.md#iostate).

- [wyjątki](#exceptions) `goodbit`zwraca .

- [flagi](../standard-library/ios-base-class.md#flags) zwraca [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags).

- [szerokość](../standard-library/ios-base-class.md#width) zwraca 0.

- [dokładność](../standard-library/ios-base-class.md#precision) zwraca 6.

- [wypełnianie](#fill) zwraca znak spacji.

- [getloc](../standard-library/ios-base-class.md#getloc) `locale::classic`zwraca .

- [iword](../standard-library/ios-base-class.md#iword) zwraca zero, a [pword](../standard-library/ios-base-class.md#pword) zwraca wskaźnik zerowy dla wszystkich wartości argumentów.

## <a name="basic_iosint_type"></a><a name="int_type"></a>basic_ios::int_type

Synonimem . `traits_type::int_type`

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_iosmove"></a><a name="move"></a>basic_ios::przenieść

Przenosi wszystkie wartości, z wyjątkiem wskaźnika do buforu strumienia, z parametru do bieżącego obiektu.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Obiekt, `ios_base` z wysuń wartości.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego przenosi wszystkie `*this` wartości przechowywane `stream buffer pointer`w *prawo,* z wyjątkiem przechowywanego , `*this`który jest niezmieniony w *prawo* i ustawiony na wskaźnik zerowy w . Przechowywany `tie pointer` jest ustawiony na wskaźnik zerowy w *prawej*.

## <a name="basic_iosnarrow"></a><a name="narrow"></a>basic_ios::wąski

Znajduje równoważny char `char_type`do danego .

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>Parametry

*Char*\
**Znak** do konwersji.

*Domyślny*\
**Char,** który ma zwrócić, jeśli nie znaleziono odpowiednika.

### <a name="return-value"></a>Wartość zwracana

Równoważny **char** do `char_type`danego .

### <a name="remarks"></a>Uwagi

Funkcja elementu [use_facet](../standard-library/basic-filebuf-class.md#open)\<członkowskiego zwraca use_facet\<ctype E> >( [getloc](../standard-library/ios-base-class.md#getloc)( ). `narrow`( `Char`, `Default`).

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

## <a name="basic_iosoff_type"></a><a name="off_type"></a>basic_ios::off_type

Synonimem . `traits_type::off_type`

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_iosoperator-void-"></a><a name="op_void_star"></a>basic_ios::nieważne operatora *

Wskazuje, czy strumień jest nadal dobry.

```cpp
operator void *() const;
```

### <a name="return-value"></a>Wartość zwracana

Operator zwraca wskaźnik zerowy tylko [wtedy, gdy nie powiedzie się](#fail).

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

## <a name="basic_iosoperator"></a><a name="op_not"></a>basic_ios::operator!

Wskazuje, czy strumień nie jest zły.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca [niepowodzenie](#fail).

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

## <a name="basic_iosoperator-bool"></a><a name="op_bool"></a>basic_ios::operator bool

Umożliwia użycie `basic_ios` obiektu jako **bool**. Automatyczna konwersja typu jest wyłączona, aby zapobiec częstym, niezamierzonych skutków ubocznych.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Uwagi

Operator zwraca wartość zamienną `fail()`na **false** tylko wtedy, gdy . Typ zwracany jest konwertowany tylko `void *` na **bool**, a nie na lub inny znany typ skalarny.

## <a name="basic_iospos_type"></a><a name="pos_type"></a>basic_ios::p_type

Synonimem . `traits_type::pos_type`

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_iosrdbuf"></a><a name="rdbuf"></a>basic_ios::rdbuf

Trasy strumienia do określonego buforu.

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>Parametry

*_Sb*\
Strumień.

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu członkowskiego zwraca wskaźnik buforu przechowywanego strumienia.

Funkcja drugiego elementu członkowskiego przechowuje *_Sb* w wskaźniku buforu przechowywanego strumienia i zwraca wcześniej przechowywaną wartość.

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

## <a name="basic_iosrdstate"></a><a name="rdstate"></a>basic_ios::rdstate

Odczytuje stan bitów dla flag.

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>Wartość zwracana

Przechowywane informacje o stanie strumienia.

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

## <a name="basic_iossetstate"></a><a name="setstate"></a>basic_ios::setstate

Ustawia dodatkowe flagi.

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>Parametry

*_state*\
Dodatkowe flagi do skonfigurowania.

### <a name="remarks"></a>Uwagi

Funkcja członkowna skutecznie wywołuje [jasne](#clear)(_ *państwo* &#124; [rdstate](#rdstate)).

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

## <a name="basic_iosset_rdbuf"></a><a name="set_rdbuf"></a>basic_ios::set_rdbuf

Przypisuje bufor strumienia do buforu odczytu dla tego obiektu strumienia.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>Parametry

*strbuf*\
Bufor strumienia, aby stać się buforem odczytu.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego przechowuje `stream buffer pointer` *strbuf* w pliku . Nie nazywa `clear`.

## <a name="basic_iostie"></a><a name="tie"></a>basic_ios::krawat

Zapewnia, że jeden strumień jest przetwarzany przed innym strumieniem.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>Parametry

*Str*\
Strumień.

### <a name="return-value"></a>Wartość zwracana

Funkcja pierwszego elementu członkowskiego zwraca zapisany wskaźnik wiązania. Druga funkcja elementu członkowskiego przechowuje *str* w wskaźniku wiązania i zwraca jego poprzednią przechowywaną wartość.

### <a name="remarks"></a>Uwagi

`tie`powoduje, że dwa strumienie mają być zsynchronizowane, tak, że operacje na jednym strumieniu występują po zakończeniu operacji na drugim strumieniu.

### <a name="example"></a>Przykład

W tym przykładzie, wiążąc cin z cout, jest gwarantowane, że ciąg "Wprowadź liczbę:" przejdzie do konsoli, zanim sam numer zostanie wyodrębniony z cin. Eliminuje to możliwość, że ciąg "Wprowadź liczbę:" nadal znajduje się w buforze, gdy numer jest odczytywany, dzięki czemu jesteśmy pewni, że użytkownik rzeczywiście ma jakiś monit, aby odpowiedzieć na. Domyślnie cin i cout są związane.

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

## <a name="basic_iostraits_type"></a><a name="traits_type"></a>basic_ios::traits_type

Synonim parametru `Traits`szablonu .

```cpp
typedef Traits traits_type;
```

## <a name="basic_ioswiden"></a><a name="widen"></a>basic_ios::widen

Znajduje odpowiednik `char_type` danego **znaku**.

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>Parametry

*Char*\
Znak do konwersji.

### <a name="return-value"></a>Wartość zwracana

Znajduje odpowiednik `char_type` danego **znaku**.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **E**> >( [getloc](../standard-library/ios-base-class.md#getloc)). `widen`( `Char`).

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

## <a name="basic_iosswap"></a><a name="swap"></a>basic_ios::swap

Wymienia wartości w `basic_ios` tym obiekcie `basic_ios` dla wartości innego obiektu. Jednak wskaźniki do buforów strumienia nie są zamienione.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Obiekt, `basic_ios` który jest używany do wymiany wartości.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego wymienia wszystkie `*this` wartości przechowywane `stream buffer pointer`w *prawo* z wyjątkiem przechowywane .

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)

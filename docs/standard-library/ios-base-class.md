---
title: ios_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- xiosbase/std::ios_base
- ios/std::ios_base::event_callback
- xiosbase/std::ios_base::fmtflags
- xiosbase/std::ios_base::iostate
- xiosbase/std::ios_base::openmode
- xiosbase/std::ios_base::seekdir
- xiosbase/std::ios_base::event
- xiosbase/std::ios_base::adjustfield
- xiosbase/std::ios_base::app
- xiosbase/std::ios_base::ate
- xiosbase/std::ios_base::badbit
- xiosbase/std::ios_base::basefield
- xiosbase/std::ios_base::beg
- xiosbase/std::ios_base::binary
- xiosbase/std::ios_base::boolalpha
- xiosbase/std::ios_base::cur
- xiosbase/std::ios_base::dec
- xiosbase/std::ios_base::end
- xiosbase/std::ios_base::eofbit
- xiosbase/std::ios_base::failbit
- xiosbase/std::ios_base::fixed
- xiosbase/std::ios_base::floatfield
- xiosbase/std::ios_base::goodbit
- xiosbase/std::ios_base::hex
- xiosbase/std::ios_base::in
- xiosbase/std::ios_base::internal
- xiosbase/std::ios_base::left
- xiosbase/std::ios_base::oct
- xiosbase/std::ios_base::out
- xiosbase/std::ios_base::right
- xiosbase/std::ios_base::scientific
- xiosbase/std::ios_base::showbase
- xiosbase/std::ios_base::showpoint
- xiosbase/std::ios_base::showpos
- xiosbase/std::ios_base::skipws
- xiosbase/std::ios_base::trunc
- xiosbase/std::ios_base::unitbuf
- xiosbase/std::ios_base::uppercase
- xiosbase/std::ios_base::failure
- xiosbase/std::ios_base::flags
- xiosbase/std::ios_base::getloc
- xiosbase/std::ios_base::imbue
- xiosbase/std::ios_base::Init
- xiosbase/std::ios_base::iword
- xiosbase/std::ios_base::precision
- xiosbase/std::ios_base::pword
- ios/std::ios_base::register_callback
- xiosbase/std::ios_base::setf
- xiosbase/std::ios_base::sync_with_stdio
- xiosbase/std::ios_base::unsetf
- xiosbase/std::ios_base::width
- xiosbase/std::ios_base::xalloc
helpviewer_keywords:
- std::ios_base [C++]
- std::ios_base [C++], event_callback
- std::ios_base [C++], fmtflags
- std::ios_base [C++], iostate
- std::ios_base [C++], openmode
- std::ios_base [C++], seekdir
- std::ios_base [C++], event
- std::ios_base [C++], adjustfield
- std::ios_base [C++], app
- std::ios_base [C++], ate
- std::ios_base [C++], badbit
- std::ios_base [C++], basefield
- std::ios_base [C++], beg
- std::ios_base [C++], binary
- std::ios_base [C++], boolalpha
- std::ios_base [C++], cur
- std::ios_base [C++], dec
- std::ios_base [C++], end
- std::ios_base [C++], eofbit
- std::ios_base [C++], failbit
- std::ios_base [C++], fixed
- std::ios_base [C++], floatfield
- std::ios_base [C++], goodbit
- std::ios_base [C++], hex
- std::ios_base [C++], in
- std::ios_base [C++], internal
- std::ios_base [C++], left
- std::ios_base [C++], oct
- std::ios_base [C++], out
- std::ios_base [C++], right
- std::ios_base [C++], scientific
- std::ios_base [C++], showbase
- std::ios_base [C++], showpoint
- std::ios_base [C++], showpos
- std::ios_base [C++], skipws
- std::ios_base [C++], trunc
- std::ios_base [C++], unitbuf
- std::ios_base [C++], uppercase
- std::ios_base [C++], failure
- std::ios_base [C++], flags
- std::ios_base [C++], getloc
- std::ios_base [C++], imbue
- std::ios_base [C++], Init
- std::ios_base [C++], iword
- std::ios_base [C++], precision
- std::ios_base [C++], pword
- std::ios_base [C++], register_callback
- std::ios_base [C++], setf
- std::ios_base [C++], sync_with_stdio
- std::ios_base [C++], unsetf
- std::ios_base [C++], width
- std::ios_base [C++], xalloc
ms.assetid: 0f9e0abc-f70f-49bc-aa1f-003859f56cfe
ms.openlocfilehash: 056b7e47c474c64bf357523e2995ef49d456a9cd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449188"
---
# <a name="iosbase-class"></a>ios_base — Klasa

Klasa zawiera opis funkcji magazynu i elementów członkowskich wspólnych dla strumieni wejściowych i wyjściowych, które nie zależą od parametrów szablonu. (Klasa szablonu [basic_ios](../standard-library/basic-ios-class.md) opisuje, co jest typowe i jest zależna od parametrów szablonu).

Obiekt klasy ios_base przechowuje informacje o formatowaniu, które składają się z:

- Formatuj flagi w obiekcie typu [fmtflags](#fmtflags).

- Maska wyjątku w obiekcie typu [iostate](#iostate).

- Szerokość pola w obiekcie typu **int**.

- Precyzja wyświetlania w obiekcie typu **int**.

- Obiekt ustawień regionalnych w obiekcie typu `locale`.

- Dwie rozszerzalne tablice z elementami typu **Long** i **void** .

Obiekt klasy ios_base również przechowuje informacje o stanie strumienia w obiekcie typu [iostate](#iostate)i stosie wywołania zwrotnego.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[ios_base](#ios_base)|Tworzy `ios_base` obiekty.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[event_callback](#event_callback)|Opisuje funkcję przekazaną do [register_call](#register_callback).|
|[fmtflags](#fmtflags)|Stałe, aby określić wygląd danych wyjściowych.|
|[iostate](#iostate)|Definiuje stałe opisujące stan strumienia.|
|[otwórzmode](#openmode)|Opisuje sposób współpracy ze strumieniem.|
|[seekdir](#seekdir)|Określa punkt początkowy dla operacji przesunięcia.|

### <a name="enums"></a>Wyliczenia

|||
|-|-|
|[event](#event)|Określa typy zdarzeń.|

### <a name="constants"></a>Stałe

|||
|-|-|
|[adjustfield](#fmtflags)|Maska bitów zdefiniowana jako `internal`. &#124; `left` &#124; `right`|
|[aplikacje](#openmode)|Określa przeszukiwanie końca strumienia przed każdym wstawieniem.|
|[Utwórz](#openmode)|Określa przeszukiwanie na końcu strumienia podczas pierwszego tworzenia obiektu sterującego.|
|[badbit](#iostate)|Rejestruje utratę integralności buforu strumienia.|
|[basefield](#fmtflags)|Maska bitów zdefiniowana jako `dec`. &#124; `hex` &#124; `oct`|
|[beg](#seekdir)|Określa odszukanie względem początku sekwencji.|
|[binarny](#openmode)|Określa, że plik powinien być odczytywany jako strumień binarny, a nie jako strumień tekstowy.|
|[boolalpha](#fmtflags)|Określa wstawianie lub Wyodrębnianie obiektów typu **bool** jako nazw (takich jak **true** i **false**), a nie jako wartości liczbowych.|
|[cur](#seekdir)|Określa odszukanie względem bieżącej pozycji w ramach sekwencji.|
|[grudzień](#fmtflags)|Określa wstawianie lub wyodrębnianie wartości całkowitych w formacie dziesiętnym.|
|[punktów](#seekdir)|Określa odszukanie względem końca sekwencji.|
|[eofbit](#iostate)|Rejestruje koniec pliku podczas wyodrębniania ze strumienia.|
|[failbit](#iostate)|Rejestruje niepowodzenie wyodrębnienia prawidłowego pola ze strumienia.|
|[FIXED](#fmtflags)|Określa wstawianie wartości zmiennoprzecinkowych w formacie stałym (bez pola wykładnika).|
|[floatfield](#fmtflags)|Maska bitów zdefiniowana jako `fixed` &#124;`scientific`|
|[goodbit](#iostate)|Wszystkie bity stanu są wyczyszczone.|
|[hex](#fmtflags)|Określa wstawianie lub wyodrębnianie wartości całkowitych w formacie szesnastkowym.|
|[in](#openmode)|Określa wyodrębnianie ze strumienia.|
|[internal](#fmtflags)|Umieszczaj w polu Szerokość pola, wstawiając znaki wypełnienia w punkcie wewnętrznym do wygenerowanego pola liczbowego.|
|[left](#fmtflags)|Określa lewe uzasadnienie.|
|[oct](#fmtflags)|Określa wstawianie lub wyodrębnianie wartości całkowitych w formacie ósemkowym.|
|[out](#openmode)|Określa wstawianie do strumienia.|
|[right](#fmtflags)|Określa odpowiednie uzasadnienie.|
|[scientific](#fmtflags)|Określa wstawianie wartości zmiennoprzecinkowych w formacie wykładniczym (z polem wykładnik).|
|[showbase](#fmtflags)|Określa wstawianie prefiksu, który ujawnia podstawę wygenerowanego pola liczb całkowitych.|
|[showpoint](#fmtflags)|Określa niewarunkowe Wstawianie przecinka dziesiętnego w wygenerowanym polu zmiennoprzecinkowym.|
|[showpos](#fmtflags)|Określa Wstawianie znaku plus w nieujemnym wygenerowanym polu liczbowym.|
|[skipws](#fmtflags)|Określa pomijanie wiodących białych znaków przed pewnymi wyciągami.|
|[TRUNC —](#openmode)|Określa usuwanie zawartości istniejącego pliku podczas tworzenia obiektu sterującego.|
|[unitbuf](#fmtflags)|Powoduje opróżnianie danych wyjściowych po każdym wstawieniu.|
|[znaki](#fmtflags)|Określa wstawianie wielkich odpowiedników małych liter w niektórych wstawieniach.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[spraw](#failure)|Klasa członkowska służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych przez funkcję członkowską [Clear](../standard-library/basic-ios-class.md#clear) w klasie template [basic_ios](../standard-library/basic-ios-class.md).|
|[znaczników](#flags)|Ustawia lub zwraca bieżące ustawienia flagi.|
|[getloc](#getloc)|Zwraca przechowywany obiekt locale.|
|[imbue](#imbue)|Zmienia ustawienia regionalne.|
|[Init](#init)|Tworzy standardowe obiekty iostream podczas konstruowania.|
|[iword](#iword)|Przypisuje wartość do zapisania jako `iword`.|
|[dokładne](#precision)|Określa liczbę cyfr, które mają być wyświetlane w liczbie zmiennoprzecinkowej.|
|[pword](#pword)|Przypisuje wartość do zapisania jako `pword`.|
|[register_callback](#register_callback)|Określa funkcję wywołania zwrotnego.|
|[setf](#setf)|Ustawia określone flagi.|
|[sync_with_stdio](#sync_with_stdio)|Zapewnia, że operacje biblioteki wykonawczej iostream i C są wykonywane w kolejności, w jakiej występują w kodzie źródłowym.|
|[unsetf](#unsetf)|Powoduje wyłączenie określonych flag.|
|[width](#width)|Ustawia długość strumienia wyjściowego.|
|[xalloc](#xalloc)|Określa, że zmienna musi być częścią strumienia.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator=](#op_eq)|Operator przypisania dla `ios_base` obiektów.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> systemu iOS

**Przestrzeń nazw:** std

## <a name="event"></a>wydarzen

Określa typy zdarzeń.

```cpp
enum event {
    erase_event,
    imbue_event,
    copyfmt_event};
```

### <a name="remarks"></a>Uwagi

Typ to typ wyliczeniowy, który opisuje obiekt, który może przechowywać zdarzenie wywołania zwrotnego użyte jako argument do funkcji zarejestrowanej w [register_callback](#register_callback). Unikatowe wartości zdarzeń to:

- `copyfmt_event`, aby zidentyfikować wywołanie zwrotne, które występuje blisko końca wywołania [copyfmt](../standard-library/basic-ios-class.md#copyfmt), tuż przed skopiowaniem [maski wyjątków](../standard-library/ios-base-class.md) .

- `erase_event`, aby zidentyfikować wywołanie zwrotne, które występuje na początku wywołania do [copyfmt](../standard-library/basic-ios-class.md#copyfmt)lub na początku wywołania destruktora  **\*.**

- `imbue_event`, aby zidentyfikować wywołanie zwrotne występujące na końcu wywołania [imbue —](#imbue), tuż przed zwróceniem funkcji.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [register_callback](#register_callback) .

## <a name="event_callback"></a>event_callback

Opisuje funkcję przekazaną do [register_call](#register_callback).

```cpp
typedef void (__cdecl *event_callback)(
    event _E,
    ios_base& _Base,
    int _I);
```

### <a name="parameters"></a>Parametry

*_E*\
[Zdarzenie](#event).

*_Base*\
Strumień, w którym wywołano zdarzenie.

*_I*\
Liczba zdefiniowana przez użytkownika.

### <a name="remarks"></a>Uwagi

Typ opisuje wskaźnik do funkcji, która może być zarejestrowana w [register_callback](#register_callback). Ten typ funkcji nie może zgłosić wyjątku.

### <a name="example"></a>Przykład

Zobacz [register_call](#register_callback) , aby uzyskać przykład, `event_callback`który używa programu.

## <a name="failure"></a>spraw

Klasa `failure` definiuje klasę bazową dla typów wszystkich obiektów zgłaszanych jako wyjątki, przez funkcje `iostreams` w bibliotece, aby raportować błędy wykryte podczas operacji buforu strumienia.

```cpp
namespace std {
    class failure : public system_error {
    public:
        explicit failure(
            const string& _Message,
            const error_code& _Code = io_errc::stream);

        explicit failure(
            const char* str,
            const error_code& _Code = io_errc::stream);
    };
}
```

### <a name="remarks"></a>Uwagi

Wartość zwrócona przez `what()` jest `_Message`kopią, prawdopodobnie uzupełnioną z testem opartym na `_Code`. Jeśli `_Code` nie jest określony, wartość domyślna to `make_error_code(io_errc::stream)`.

### <a name="example"></a>Przykład

```cpp
// ios_base_failure.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.exceptions(ios::failbit);
    try
    {
        file.open( "rm.txt", ios_base::in );
        // Opens nonexistent file for reading
    }
    catch( ios_base::failure f )
    {
        cout << "Caught an exception: " << f.what() << endl;
    }
}
```

```Output
Caught an exception: ios_base::failbit set
```

## <a name="flags"></a>znaczników

Ustawia lub zwraca bieżące ustawienia flagi.

```cpp
fmtflags flags() const;
fmtflags flags(fmtflags fmtfl);
```

### <a name="parameters"></a>Parametry

*fmtfl*\
Nowe `fmtflags` ustawienie.

### <a name="return-value"></a>Wartość zwracana

Poprzednie lub bieżące `fmtflags` ustawienie.

### <a name="remarks"></a>Uwagi

Aby uzyskać listę flag, zobacz [ios_base:: fmtflags](#fmtflags) .

Pierwsza funkcja członkowska zwraca flagi formatu przechowywanego. Druga funkcja członkowska przechowuje *fmtfl* w flagach formatu i zwraca jego poprzednią wartość przechowywaną.

### <a name="example"></a>Przykład

```cpp
// ios_base_flags.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    cout << cout.flags( ) << endl;
    cout.flags( ios::dec | ios::boolalpha );
    cout << cout.flags( );
}
```

```Output
513
16896
```

## <a name="fmtflags"></a>fmtflags

Stałe, aby określić wygląd danych wyjściowych.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type fmtflags;
   static const fmtflags boolalpha;
   static const fmtflags dec;
   static const fmtflags fixed;
   static const fmtflags hex;
   static const fmtflags internal;
   static const fmtflags left;
   static const fmtflags oct;
   static const fmtflags right;
   static const fmtflags scientific;
   static const fmtflags showbase;
   static const fmtflags showpoint;
   static const fmtflags showpos;
   static const fmtflags skipws;
   static const fmtflags unitbuf;
   static const fmtflags uppercase;
   static const fmtflags adjustfield;
   static const fmtflags basefield;
   static const fmtflags floatfield;
   // ...
};
```

### <a name="remarks"></a>Uwagi

Obsługuje manipulowanie w systemie [iOS](../standard-library/ios.md).

Typ jest typem maski bitowej, który opisuje obiekt, który może przechowywać flagi formatowania. Unikatowe wartości flag (elementy) to:

- `dec`, aby wstawić lub wyodrębnić wartości całkowite w formacie dziesiętnym.

- `hex`, aby wstawić lub wyodrębnić wartości całkowite w formacie szesnastkowym.

- `oct`, aby wstawić lub wyodrębnić wartości całkowite w formacie ósemkowym.

- `showbase`, aby wstawić prefiks, który pokazuje podstawę wygenerowanego pola liczba całkowita.

- `internal`, aby dopełnić do szerokości pola, w razie potrzeby wstawiając znaki wypełnienia w punkcie wewnętrznym do wygenerowanego pola liczbowego. (Aby uzyskać informacje na temat ustawiania szerokości pola, zobacz [setw](../standard-library/iomanip-functions.md#setw)).

- `left`, aby dokończyć do szerokości pola, w razie potrzeby wstawiając znaki wypełnienia na końcu wygenerowanego pola (lewe uzasadnienie).

- `right`, aby dopełnić do szerokości pola, w razie potrzeby wstawiając znaki wypełnienia na początku wygenerowanego pola (Justowanie do prawej).

- `boolalpha`, aby wstawić lub wyodrębnić obiekty typu **bool** jako nazwy (takie jak **true** i **false**), a nie jako wartości liczbowe.

- `fixed`, aby wstawić wartości zmiennoprzecinkowe w formacie stałym (bez pola wykładnik).

- `scientific`, aby wstawić wartości zmiennoprzecinkowe w formacie naukowym (z polem wykładnik).

- `showpoint`, aby wstawić bezwarunkowo punkt dziesiętny w wygenerowanym polu zmiennoprzecinkowym.

- `showpos`, aby wstawić znak plus w nieujemnym wygenerowanym polu liczbowym.

- `skipws`, aby pominąć odstępy wiodące przed pewnymi wyciągami.

- `unitbuf`, aby opróżnić dane wyjściowe po każdym wstawieniu.

- `uppercase`, aby wstawić wielkie litery małych liter w niektórych wstawieniach.

Ponadto kilka przydatnych wartości to:

- `adjustfield`, maska bitów zdefiniowana jako `internal` &#124; `left` &#124;`right`

- `basefield`, zdefiniowane jako `dec` &#124; `hex` &#124;`oct`

- `floatfield`, zdefiniowane jako `fixed` &#124;`scientific`

Przykłady funkcji modyfikujących te flagi formatu można znaleźć w temacie [ \<iomanip >](../standard-library/iomanip.md).

## <a name="getloc"></a>getloc

Zwraca przechowywany obiekt locale.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Wartość zwracana

Przechowywany obiekt locale.

### <a name="example"></a>Przykład

```cpp
// ios_base_getlock.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << cout.getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="imbue"></a>imbue —

Zmienia ustawienia regionalne.

```cpp
locale imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*\
Nowe ustawienie regionalne.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienia regionalne.

### <a name="remarks"></a>Uwagi

Funkcja członkowska przechowuje *_Loc* w obiekcie Locals, a następnie raportuje zdarzenie wywołania `imbue_event`zwrotnego i. Zwraca poprzednią wartość przechowywaną.

### <a name="example"></a>Przykład

Aby uzyskać przykład, zobacz [basic_ios:: imbue —](../standard-library/basic-ios-class.md#imbue) .

## <a name="init"></a>Init

Tworzy standardowe obiekty iostream podczas konstruowania.

```cpp
class Init { };
```

### <a name="remarks"></a>Uwagi

Klasa zagnieżdżona opisuje obiekt, którego konstrukcja gwarantuje, że standardowe obiekty iostreams są prawidłowo skonstruowane, nawet przed wykonaniem konstruktora dla dowolnego obiektu statycznego.

## <a name="ios_base"></a>ios_base

Tworzy obiekty ios_base.

```cpp
ios_base();
```

### <a name="remarks"></a>Uwagi

Konstruktor (Protected) nie robi nic. Późniejsze wywołanie **basic_ios::** [init](../standard-library/basic-ios-class.md#init) musi inicjować obiekt, zanim będzie można je bezpiecznie zniszczyć. W tym celu jedynym bezpiecznym zastosowaniem klasy ios_base jest klasa bazowa dla klasy szablonu [basic_ios](../standard-library/basic-ios-class.md).

## <a name="iostate"></a>iostate

Typ stałych opisujących stan strumienia.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type iostate;
   static const iostate badbit;
   static const iostate eofbit;
   static const iostate failbit;
   static const iostate goodbit;
   // ...
};
```

### <a name="remarks"></a>Uwagi

Typ jest typem maski bitowej, który opisuje obiekt, który może przechowywać informacje o stanie strumienia. Unikatowe wartości flag (elementy) to:

- `badbit`, aby zarejestrować utratę integralności buforu strumienia.

- `eofbit`, aby zarejestrować koniec pliku podczas wyodrębniania ze strumienia.

- `failbit`, aby zarejestrować niepowodzenie wyodrębnienia prawidłowego pola ze strumienia.

Ponadto przydatną wartością jest `goodbit`, gdy żadna z wymienionych wcześniej bitów nie jest ustawiona (`goodbit` gwarantowany jest zero).

## <a name="iword"></a>iword

Przypisuje wartość do zapisania jako `iword`.

```cpp
long& iword(int idx);
```

### <a name="parameters"></a>Parametry

*IDX*\
Indeks wartości do zapisania jako `iword`.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca odwołanie do elementu *IDX* rozszerzalnej tablicy z elementami typu **Long**. Wszystkie elementy są efektywnie obecne i początkowo przechowują wartość zero. Zwrócone odwołanie jest nieprawidłowe po następnym wywołaniu `iword` dla obiektu, po zmianie obiektu przez wywołanie **basic_ios::** [copyfmt](../standard-library/basic-ios-class.md#copyfmt)lub po zniszczeniu obiektu.

Jeśli *IDX* jest ujemny lub jeśli unikatowy magazyn jest niedostępny dla elementu, funkcja wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate) **(badbit)** i zwraca odwołanie, które może nie być unikatowe.

Aby uzyskać unikatowy indeks do użycia we wszystkich obiektach typu `ios_base`, wywołaj [xalloc](#xalloc).

### <a name="example"></a>Przykład

Zobacz [xalloc](#xalloc) , aby uzyskać przykład użycia `iword`.

## <a name="openmode"></a>otwórzmode

Opisuje sposób współpracy ze strumieniem.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type iostate;
   static const iostate badbit;
   static const iostate eofbit;
   static const iostate failbit;
   static const iostate goodbit;
   // ...
};
```

### <a name="remarks"></a>Uwagi

Typ to `bitmask type` , który opisuje obiekt, który może przechowywać tryb otwierania dla kilku obiektów iostreams. Unikatowe wartości flag (elementy) to:

- `app`, aby przejść do końca strumienia przed każdym wstawieniem.

- `ate`, aby przejść do końca strumienia podczas pierwszego tworzenia obiektu sterującego.

- `binary`, aby odczytywać plik jako strumień binarny, a nie jako strumień tekstowy.

- `in`, aby zezwolić na wyodrębnianie ze strumienia.

- `out`, aby zezwolić na wstawianie do strumienia.

- `trunc`, aby usunąć zawartość istniejącego pliku po utworzeniu obiektu sterującego.

### <a name="example"></a>Przykład

```cpp
// ios_base_openmode.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.open( "rm.txt", ios_base::out | ios_base::trunc );

    file << "testing";
}
```

## <a name="op_eq"></a>operator =

Operator przypisania dla obiektów ios_base.

```cpp
ios_base& operator=(const ios_base& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt typu `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Obiekt, do którego jest przypisany.

### <a name="remarks"></a>Uwagi

Operator kopiuje przechowywane informacje o formatowaniu, tworząc nową kopię dowolnych rozszerzalnych tablic. Następnie zwraca  **\*to**. Należy zauważyć, że stos wywołania zwrotnego nie jest kopiowany.

Ten operator jest używany tylko przez klasy pochodne od `ios_base`.

## <a name="precision"></a>dokładne

Określa liczbę cyfr, które mają być wyświetlane w liczbie zmiennoprzecinkowej.

```cpp
streamsize precision() const;
streamsize precision(streamsize _Prec);
```

### <a name="parameters"></a>Parametry

*_Prec*\
Liczba cyfr znaczących do wyświetlenia lub liczba cyfr po przecinku dziesiętnym w stałej notacji.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja członkowska zwraca zachowaną [precyzję wyświetlania](../standard-library/ios-base-class.md). Druga funkcja członkowska przechowuje *_Prec* z dokładnością wyświetlania i zwraca swoją poprzednią przechowywaną wartość.

### <a name="remarks"></a>Uwagi

Liczby zmiennoprzecinkowe są wyświetlane w stałych notacjach ze [stałym](../standard-library/ios-functions.md#fixed)tekstem.

### <a name="example"></a>Przykład

```cpp
// ios_base_precision.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    float i = 31.31234F;

    cout.precision( 3 );
    cout << i << endl;          // display three significant digits
    cout << fixed << i << endl; // display three digits after decimal
                                // point
}
```

```Output
31.3
31.312
```

## <a name="pword"></a>pword

Przypisuje wartość do zapisania jako `pword`.

```cpp
void *& pword(int _Idx);
```

### <a name="parameters"></a>Parametry

*_Idx*\
Indeks wartości do zapisania jako `pword`.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca odwołanie do *elementu _ dla* rozszerzalnej tablicy z elementami typu **void** . Wszystkie elementy są efektywnie obecne i początkowo przechowują wskaźnik o wartości null. Zwrócone odwołanie jest nieprawidłowe po następnym wywołaniu `pword` dla obiektu, po zmianie obiektu przez wywołanie **basic_ios::** [copyfmt](../standard-library/basic-ios-class.md#copyfmt)lub po zniszczeniu obiektu.

Jeśli _ *IDX* jest ujemna lub jeśli unikatowy magazyn jest niedostępny dla elementu, funkcja wywołuje metodę setstate [](../standard-library/basic-ios-class.md#setstate) **(badbit)** i zwraca odwołanie, które może nie być unikatowe.

Aby uzyskać unikatowy indeks do użycia we wszystkich obiektach typu `ios_base`, wywołaj [xalloc](#xalloc).

### <a name="example"></a>Przykład

Zobacz [xalloc](#xalloc) , aby poznać przykład użycia `pword`.

## <a name="register_callback"></a>register_callback

Określa funkcję wywołania zwrotnego.

```cpp
void register_callback(
    event_callback pfn, int idx);
```

### <a name="parameters"></a>Parametry

*PFN*\
Wskaźnik do funkcji wywołania zwrotnego.

*IDX*\
Liczba zdefiniowana przez użytkownika.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wypychanie pary `{pfn, idx}` do przechowywanego [stosu wywołań zwrotnych](../standard-library/ios-base-class.md)stosu wywołań zwrotnych. Gdy zgłaszane jest raportowanie **zdarzeń wywołania** zwrotnego, funkcje są wywoływane, w odwrotnej kolejności rejestru, przez wyrażenie `(*pfn)(ev, *this, idx)`.

### <a name="example"></a>Przykład

```cpp
// ios_base_register_callback.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void callback1( ios_base::event e, ios_base& stream, int arg )
{
    cout << "in callback1" << endl;
    switch ( e )
    {
    case ios_base::erase_event:
        cout << "an erase event" << endl;
        break;
    case ios_base::imbue_event:
        cout << "an imbue event" << endl;
        break;
    case ios_base::copyfmt_event:
        cout << "an copyfmt event" << endl;
        break;
    };
}

void callback2( ios_base::event e, ios_base& stream, int arg )
{
    cout << "in callback2" << endl;
    switch ( e )
    {
    case ios_base::erase_event:
        cout << "an erase event" << endl;
        break;
    case ios_base::imbue_event:
        cout << "an imbue event" << endl;
        break;
    case ios_base::copyfmt_event:
        cout << "an copyfmt event" << endl;
        break;
    };
}

int main( )
{
    // Make sure the imbue will not throw an exception
    // assert( setlocale( LC_ALL, "german" )!=NULL );

    cout.register_callback( callback1, 0 );
    cin.register_callback( callback2, 0 );

    try
    {
        // If no exception because the locale's not found,
        // generate an imbue_event on callback1
        cout.imbue(locale("german"));
    }
    catch(...)
    {
        cout << "exception" << endl;
    }

    // This will
    // (1) erase_event on callback1
    // (2) copyfmt_event on callback2
    cout.copyfmt(cin);

    // We get two erase events from callback2 at the end because
    // both cin and cout have callback2 registered when cin and cout
    // are destroyed at the end of program.
}
```

```Output
in callback1
an imbue event
in callback1
an erase event
in callback2
an copyfmt event
in callback2
an erase event
in callback2
an erase event
```

## <a name="seekdir"></a>seekdir

Określa punkt początkowy dla operacji przesunięcia.

```cpp
namespace std {
    class ios_base {
    public:
        typedef implementation-defined-enumerated-type seekdir;
        static const seekdir beg;
        static const seekdir cur;
        static const seekdir end;
        // ...
    };
}
```

### <a name="remarks"></a>Uwagi

Typ to typ wyliczeniowy, który opisuje obiekt, który może przechowywać Tryb wyszukiwania używany jako argument do funkcji składowych kilku klas iostream. Wartości flag DISTINCT są następujące:

- `beg`, aby przeszukać (zmienić bieżącą pozycję odczytu lub zapisu) względem początku sekwencji (tablicy, strumienia lub pliku).

- `cur`, aby przejść względem bieżącej pozycji w ramach sekwencji.

- `end`, aby przejść względem końca sekwencji.

### <a name="example"></a>Przykład

```cpp
// ios_base_seekdir.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.open( "rm.txt", ios_base::out | ios_base::trunc );

    file << "testing";
    file.seekp( 0, ios_base::beg );
    file << "a";
    file.seekp( 0, ios_base::end );
    file << "a";
}
```

## <a name="setf"></a>setf

Ustawia określone flagi.

```cpp
fmtflags setf(
    fmtflags _Mask
);
fmtflags setf(
    fmtflags _Mask,
    fmtflags _Unset
);
```

### <a name="parameters"></a>Parametry

*_Mask*\
Flagi do włączenia.

*_Unset*\
Flagi, które należy wyłączyć.

### <a name="return-value"></a>Wartość zwracana

Poprzednie flagi formatu

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska skutecznie wywołuje [flagi](#flags)(  *\_*  *\_flagi*maski &#124; ) (ustawia wybrane bity), a następnie zwraca poprzednie flagi formatu. Druga funkcja członkowska skutecznie wywołuje `flags(_Mask & fmtfl, flags & ~_Mask)` (Zastąp wybrane bity w ramach maski), a następnie zwraca poprzednie flagi formatu.

### <a name="example"></a>Przykład

```cpp
// ios_base_setf.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    int i = 10;
    cout << i << endl;

    cout.unsetf( ios_base::dec );
    cout.setf( ios_base::hex );
    cout << i << endl;

    cout.setf( ios_base::dec );
    cout << i << endl;
    cout.setf( ios_base::hex, ios_base::dec );
    cout << i << endl;
}
```

## <a name="sync_with_stdio"></a>sync_with_stdio

Zapewnia, że operacje biblioteki wykonawczej iostream i C są wykonywane w kolejności, w jakiej występują w kodzie źródłowym.

```cpp
static bool sync_with_stdio(
   bool _Sync = true
);
```

### <a name="parameters"></a>Parametry

*_Sync*\
Czy wszystkie strumienie są zsynchronizowane `stdio`z programem.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienie tej funkcji.

### <a name="remarks"></a>Uwagi

Statyczna funkcja członkowska przechowuje `stdio` flagę synchronizacji, która jest początkowo **prawdziwa**. Gdy **ma wartość true**, ta flaga gwarantuje, że operacje w tym samym pliku są prawidłowo synchronizowane między funkcjami [iostreams](../standard-library/iostreams-conventions.md) i tymi zdefiniowanymi w bibliotece C++ standardowej. W przeciwnym razie Synchronizacja może być niegwarantowana, ale wydajność może zostać ulepszona. Funkcja przechowuje *_Sync* w `stdio` flagi synchronizacji i zwraca jego poprzednią przechowywaną wartość. Można ją niezawodnie wywołać tylko przed wykonaniem jakichkolwiek operacji na strumieniach standardowych.

## <a name="unsetf"></a>unsetf

Powoduje wyłączenie określonych flag.

```cpp
void unsetf(
   fmtflags _Mask
);
```

### <a name="parameters"></a>Parametry

*_Mask*\
Flagi, które chcesz wyłączyć.

### <a name="remarks"></a>Uwagi

Funkcja członkowska skutecznie wywołuje [flagi](#flags)(`~` *_Mask* **& flags**) (wyczyść wybrane bity).

### <a name="example"></a>Przykład

Zobacz [ios_base:: setf](#setf) , aby uzyskać przykład użycia `unsetf`.

## <a name="width"></a>Szerokość

Ustawia długość strumienia wyjściowego.

```cpp
streamsize width( ) const;
streamsize width(
   streamsize _Wide
);
```

### <a name="parameters"></a>Parametry

*_Wide*\
Żądany rozmiar strumienia wyjściowego.

### <a name="return-value"></a>Wartość zwracana

Ustawienie bieżącej szerokości.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca wartość przechowywanej szerokości pola. Druga funkcja członkowska przechowuje *_Wide* w szerokości pola i zwraca jego poprzednią wartość przechowywaną.

### <a name="example"></a>Przykład

```cpp
// ios_base_width.cpp
// compile with: /EHsc
#include <iostream>

int main( ) {
    using namespace std;

    cout.width( 20 );
    cout << cout.width( ) << endl;
    cout << cout.width( ) << endl;
}
```

```Output
20
0
```

## <a name="xalloc"></a>xalloc

Określa, że zmienna jest częścią strumienia.

```cpp
static int xalloc( );
```

### <a name="return-value"></a>Wartość zwracana

Statyczna funkcja członkowska zwraca przechowywaną wartość statyczną, która zwiększa się w każdym wywołaniu.

### <a name="remarks"></a>Uwagi

Można użyć wartości zwracanej jako unikatowego argumentu indeksu podczas wywoływania funkcji Członkowskich [iword](#iword) lub [pword](#pword).

### <a name="example"></a>Przykład

```cpp
// ios_base_xalloc.cpp
// compile with: /EHsc
// Lets you store user-defined information.
// iword, jword, xalloc
#include <iostream>

int main( )
{
    using namespace std;

    static const int i = ios_base::xalloc();
    static const int j = ios_base::xalloc();
    cout.iword( i ) = 11;
    cin.iword( i ) = 13;
    cin.pword( j ) = "testing";
    cout << cout.iword( i ) << endl;
    cout << cin.iword( i ) << endl;
    cout << ( char * )cin.pword( j ) << endl;
}
```

```Output
11
13
testing
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)

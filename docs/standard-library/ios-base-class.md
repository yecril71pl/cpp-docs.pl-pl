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
ms.openlocfilehash: 3c9b1081a7e2ccd45c64c1cbcd833dcda9470f7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648672"
---
# <a name="iosbase-class"></a>ios_base — Klasa

Klasa opisuje magazynu i funkcje Członkowskie wspólne dla danych wejściowych i wyjściowych strumieni, które nie są zależne od parametrów szablonu. (Klasy szablonu [basic_ios —](../standard-library/basic-ios-class.md) opisuje co to jest typowe i jest zależna od parametrów szablonu.)

Obiekt ios_base — klasa przechowuje informacje o formatowaniu, która obejmuje:

- Formatowanie flagi w obiekcie typu [fmtflags](#fmtflags).

- Maska wyjątku w obiekcie typu [iostate](#iostate).

- Szerokość pola w obiekcie typu **int**.

- Precyzją wyświetlania, w obiekcie typu **int**.

- Obiekt ustawień regionalnych w obiekcie typu `locale`.

- Dwie tablice rozszerzalny, elementami typu **długie** i **void** wskaźnika.

Obiekt ios_base — klasa przechowuje także informacje o stanie strumienia, w obiekcie typu [iostate](#iostate)i stosu wywołań zwrotnych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[ios_base](#ios_base)|Konstruuje `ios_base` obiektów.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[event_callback](#event_callback)|W tym artykule opisano przekazany do funkcji [register_call](#register_callback).|
|[fmtflags](#fmtflags)|Stałe, aby określić sposób wyświetlania danych wyjściowych.|
|[iostate](#iostate)|Definiuje stałe opisujące stan strumienia.|
|[openmode](#openmode)|W tym artykule opisano sposób interakcji ze strumieniem.|
|[seekdir](#seekdir)|Określa punkt początkowy dla operacji przesunięcia.|

### <a name="enums"></a>Wyliczenia

|||
|-|-|
|[event](#event)|Określa typy zdarzeń.|

### <a name="constants"></a>Stałe

|||
|-|-|
|[adjustfield](#fmtflags)|Maska bitowa zdefiniowany jako `internal` &#124; `left` &#124; `right`.|
|[Aplikacja](#openmode)|Określa, wyszukiwanie na koniec strumienia przed każdym wstawiania.|
|[Utwórz](#openmode)|Określa, wyszukiwanie do końca strumienia, w chwili utworzenia jej kontrolowania obiektu.|
|[badbit](#iostate)|Rejestruje utraty integralności buforu strumienia.|
|[basefield](#fmtflags)|Maska bitowa zdefiniowany jako `dec` &#124; `hex` &#124; `oct`.|
|[beg](#seekdir)|Określa względem początku sekwencji.|
|[dane binarne](#openmode)|Określa, że plik powinny być odczytywane jako strumienia binarnego, a nie jako strumienia tekstu.|
|[boolalpha](#fmtflags)|Określa wstawiania lub wyodrębniania obiektów typu **bool** jako nazwy (takie jak **true** i **false**), a nie jako wartości liczbowe.|
|[cur](#seekdir)|Określa względem początku bieżącej pozycji w sekwencji.|
|[Gru](#fmtflags)|Określa wstawiania lub ekstrakcji liczb całkowitych w formacie dziesiętnym.|
|[koniec](#seekdir)|Określa względem końca sekwencji.|
|[eofbit](#iostate)|Rekordy koniec pliku podczas wyodrębniania ze strumienia.|
|[failbit](#iostate)|Rejestruje błąd podczas wyodrębniania prawidłowym polem ze strumienia.|
|[Stała](#fmtflags)|Określa różne wartości zmiennoprzecinkowe operacje wstawiania w formatu stałoprzecinkowego (z Brak wykładnika pola).|
|[floatfield](#fmtflags)|Maska bitowa zdefiniowany jako `fixed`&#124; `scientific`|
|[goodbit](#iostate)|Wyczyść wszystkie bity stanu.|
|[hex](#fmtflags)|Określa wstawiania lub ekstrakcji liczb całkowitych w formacie szesnastkowym.|
|[in](#openmode)|Określa wyodrębniania ze strumienia.|
|[internal](#fmtflags)|Okienka do szerokości pola, wstawiając znaki w punkcie wewnętrzne wygenerowanego pola liczbowego.|
|[left](#fmtflags)|Określa uzasadnienie po lewej stronie.|
|[oct](#fmtflags)|Określa wstawiania lub ekstrakcji liczb całkowitych w formacie.|
|[out](#openmode)|Określa wstawiania do strumienia.|
|[right](#fmtflags)|Określa prawej strony.|
|[scientific](#fmtflags)|Określa wstawiania wartości zmiennoprzecinkowych w formacie naukowym (z polem wykładnika).|
|[showbase](#fmtflags)|Określa wstawiania prefiks, który ujawnia base pola wygenerowana liczba całkowita.|
|[showpoint](#fmtflags)|Określa bezwarunkowe Wstawianie przecinka dziesiętnego w wygenerowanym pola zmiennoprzecinkowego.|
|[showpos](#fmtflags)|Określa wstawiania znak plus w nieujemna wygenerowanego pola liczbowego.|
|[skipws](#fmtflags)|Określa, pomijanie wiodących biały znak przed niektórych wyodrębniania.|
|[TRUNC —](#openmode)|Określa zawartość usuwania istniejącego pliku, gdy jego kontrolowanie obiekt zostanie utworzony.|
|[unitbuf](#fmtflags)|Powoduje, że dane wyjściowe do opróżniany po każdym wstawiania.|
|[wielkie litery](#fmtflags)|Określa wstawiania odpowiedniki wielkie litery, małe litery, w niektórych wstawienia.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Błąd](#failure)|Klasa elementu członkowskiego służy jako klasa bazowa dla wszystkich wyjątków generowanych przez funkcję elementu członkowskiego [wyczyść](../standard-library/basic-ios-class.md#clear) w klasie szablonu [basic_ios —](../standard-library/basic-ios-class.md).|
|[flagi](#flags)|Ustawia lub zwraca bieżące ustawienia flagi.|
|[getloc](#getloc)|Zwraca obiekt ustawień regionalnych przechowywanych.|
|[imbue](#imbue)|Zmiany ustawień regionalnych.|
|[Init](#init)|Tworzy obiektów standardowa iostream, kiedy zostaną wykonane.|
|[iword](#iword)|Przypisuje wartość do zapisania jako `iword`.|
|[Precyzja](#precision)|Określa liczbę cyfr wyświetlanych w liczbę zmiennoprzecinkową.|
|[pword —](#pword)|Przypisuje wartość do zapisania jako `pword`.|
|[register_callback](#register_callback)|Określa funkcję wywołania zwrotnego.|
|[SETF](#setf)|Ustawia określone flagi.|
|[sync_with_stdio](#sync_with_stdio)|Zapewnia, że iostream i operacje biblioteki wykonawczej C wystąpić w kolejności, w jakiej występują w kodzie źródłowym.|
|[unsetf —](#unsetf)|Powoduje, że określone flagi były wyłączone.|
|[width](#width)|Ustawia długość strumienia wyjściowego.|
|[xalloc](#xalloc)|Określa, że zmienna jest części strumienia.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Operator przypisania dla `ios_base` obiektów.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<dla systemu ios >

**Namespace:** standardowe

## <a name="event"></a>  ios_base::Event

Określa typy zdarzeń.

```cpp
enum event {
    erase_event,
    imbue_event,
    copyfmt_event};
```

### <a name="remarks"></a>Uwagi

Typ jest typem wyliczanym, który opisuje obiekt, który może przechowywać zdarzenia wywołania zwrotnego używane jako argument do funkcji zarejestrowane w usłudze [register_callback —](#register_callback). Wartości różnych zdarzeń są następujące:

- `copyfmt_event`, do identyfikowania wywołanie zwrotne, które występuje w końcowej części wywołanie [copyfmt —](../standard-library/basic-ios-class.md#copyfmt), tuż przed [maskę wyjątku](../standard-library/ios-base-class.md) jest kopiowany.

- `erase_event`, aby zidentyfikować wywołania zwrotnego, która występuje na początku wywołanie [copyfmt —](../standard-library/basic-ios-class.md#copyfmt), lub na początku po wywołaniu destruktora dla  **\*to**.

- `imbue_event`, aby zidentyfikować wywołania zwrotnego, która występuje na końcu wywołania [imbue —](#imbue), po prostu, zanim funkcja zwróci.

### <a name="example"></a>Przykład

Zobacz [register_callback —](#register_callback) przykład.

## <a name="event_callback"></a>  ios_base::event_callback

W tym artykule opisano przekazany do funkcji [register_call](#register_callback).

```cpp
typedef void (__cdecl *event_callback)(
    event _E,
    ios_base& _Base,
    int _I);
```

### <a name="parameters"></a>Parametry

*_E*<br/>
[Zdarzeń](#event).

*_Podstawowego*<br/>
Strumień, w której wywołano zdarzenie.

*_I*<br/>
Liczba zdefiniowanych przez użytkownika.

### <a name="remarks"></a>Uwagi

Typ opisuje wskaźnik do funkcji, która może być zarejestrowany w usłudze [register_callback —](#register_callback). Ten typ funkcji nie może zgłaszać wyjątek.

### <a name="example"></a>Przykład

Zobacz [register_call](#register_callback) przykład, który używa `event_callback`.

## <a name="failure"></a>  ios_base::failure

Klasa `failure` definiuje klasę bazową dla typów wszystkich obiektów generowane jako wyjątki, przez funkcje w `iostreams` biblioteki zgłaszaj błędy wykryte podczas operacji buforu strumienia.

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

Wartość zwrócona przez obiekt `what()` jest kopią `_Message`, prawdopodobnie rozszerzone testu na podstawie `_Code`. Jeśli `_Code` nie zostanie określony, wartością domyślną jest `make_error_code(io_errc::stream)`.

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

## <a name="flags"></a>  ios_base::Flags

Ustawia lub zwraca bieżące ustawienia flagi.

```cpp
fmtflags flags() const;
fmtflags flags(fmtflags fmtfl);
```

### <a name="parameters"></a>Parametry

*fmtfl*<br/>
Nowy `fmtflags` ustawienie.

### <a name="return-value"></a>Wartość zwracana

Poprzednie lub bieżącego `fmtflags` ustawienie.

### <a name="remarks"></a>Uwagi

Zobacz [ios_base::fmtflags](#fmtflags) listę flag.

Pierwsza funkcja elementu członkowskiego zwraca flagi formatu przechowywanych. Drugi magazynów funkcja elementu członkowskiego *fmtfl* flagi formatu i zwraca jego poprzedniej przechowywaną wartość.

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

## <a name="fmtflags"></a>  ios_base::fmtflags

Stałe, aby określić sposób wyświetlania danych wyjściowych.

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

Obsługuje manipulatory w [ios](../standard-library/ios.md).

Typ jest typem maski bitów, który opisuje obiekt, które mogą być przechowywane flagi formatu. Flagi odrębne wartości (elementy) są następujące:

- `dec`, aby wstawić lub Wyodrębnij wartości całkowite w formacie dziesiętnym.

- `hex`, aby wstawić lub Wyodrębnij wartości całkowite w formacie szesnastkowym.

- `oct`, aby wstawić lub Wyodrębnij wartości całkowite w formacie.

- `showbase`, aby wstawić prefiks, który ujawnia base pola wygenerowana liczba całkowita.

- `internal`, aby uzupełnić do szerokości pola, zgodnie z potrzebami, wstawiając znaki w punkcie wewnętrzne wygenerowanego pola liczbowego. (Aby uzyskać informacje na temat ustawiania szerokości pola, zobacz [setw](../standard-library/iomanip-functions.md#setw)).

- `left`, aby uzupełnić do szerokości pola, zgodnie z potrzebami, wstawiając znaki na końcu wygenerowanego pola (uzasadnienie po lewej stronie).

- `right`, aby uzupełnić do szerokości pola, zgodnie z potrzebami, wstawiając znaki na początku wygenerowanego pola (prawej strony).

- `boolalpha`, aby wstawić lub Wyodrębnij obiektów typu **bool** jako nazwy (takie jak **true** i **false**), a nie jako wartości liczbowe.

- `fixed`, aby wstawić wartości zmiennoprzecinkowych formatu stałoprzecinkowego (z Brak wykładnika pola).

- `scientific`, aby wstawić wartości zmiennoprzecinkowych w formacie naukowym (z polem wykładnika).

- `showpoint`, aby wstawić separator dziesiętny bezwarunkowo wygenerowanego pola zmiennoprzecinkowego.

- `showpos`, aby wstawić znak plus nieujemna wygenerowanego pola liczbowego.

- `skipws`, aby pominąć wiodących biały znak przed niektórych wyodrębniania.

- `unitbuf`, aby opróżnić danych wyjściowych po każdym wstawiania.

- `uppercase`, aby wstawić odpowiedniki wielkie litery, małe litery w niektórych wstawienia.

Ponadto kilka wartości przydatne to:

- `adjustfield`, maskę bitów zdefiniowany jako `internal` &#124; `left`&#124; `right`

- `basefield`, zdefiniowane jako `dec` &#124; `hex`&#124; `oct`

- `floatfield`, zdefiniowane jako `fixed`&#124; `scientific`

Aby uzyskać przykłady funkcji, które modyfikują je sformatować flagi, zobacz [ \<iomanip >](../standard-library/iomanip.md).

## <a name="getloc"></a>  ios_base::getloc

Zwraca obiekt ustawień regionalnych przechowywanych.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt przechowywanych ustawień regionalnych.

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

## <a name="imbue"></a>  ios_base::imbue

Zmiany ustawień regionalnych.

```cpp
locale imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*<br/>
Nowe ustawienie regionalne.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienia regionalne.

### <a name="remarks"></a>Uwagi

Magazyny funkcja elementu członkowskiego *_Loc* w obiekcie ustawień regionalnych i następnie zgłasza zdarzenie wywołania zwrotnego i `imbue_event`. Zwraca poprzednią wartość przechowywanych.

### <a name="example"></a>Przykład

Zobacz [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue) dla próbki.

## <a name="init"></a>  ios_base::init

Tworzy obiektów standardowa iostream, kiedy zostaną wykonane.

```cpp
class Init { };
```

### <a name="remarks"></a>Uwagi

Zagnieżdżona klasa opisująca obiekt, którego konstrukcji gwarantuje, że obiekty iostreams standardowych prawidłowo są konstruowane, nawet przed wykonaniem konstruktora dla dowolnego obiektu statycznego.

## <a name="ios_base"></a>  ios_base::ios_base

Tworzy obiekty ios_base —.

```cpp
ios_base();
```

### <a name="remarks"></a>Uwagi

Konstruktor (chroniony) nie działa. Nowsze wywołanie **basic_ios —::**[init](../standard-library/basic-ios-class.md#init) należy zainicjować obiektu, zanim może zostać bezpiecznie zniszczone. W związku z tym, tylko bezpieczne użycie ios_base — klasa jest jako klasę bazową dla klasy szablonu [basic_ios —](../standard-library/basic-ios-class.md).

## <a name="iostate"></a>  ios_base::iostate

Typ stałych, które opisują stan strumienia.

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

Typ jest typem maski bitów, który opisuje obiekt, który może przechowywać informacje o stanie strumienia. Flagi odrębne wartości (elementy) są następujące:

- `badbit`, aby nagrać utraty integralności buforu strumienia.

- `eofbit`, aby rekordów koniec pliku podczas wyodrębniania ze strumienia.

- `failbit`, aby zarejestrować błąd podczas wyodrębniania prawidłowym polem ze strumienia.

Ponadto jest przydatny wartość `goodbit`, gdzie wymienionych wcześniej bity są ustawione (`goodbit` może być równy zero).

## <a name="iword"></a>  ios_base::iword

Przypisuje wartość do zapisania jako `iword`.

```cpp
long& iword(int idx);
```

### <a name="parameters"></a>Parametry

*idx*<br/>
Indeks wartości do przechowywania jako `iword`.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do elementu *idx* tablicy extensible elementami typu **długie**. Wszystkie elementy są wydajnie obecne i początkowo przechowywane wartości zero. Zwracane odwołanie będzie nieprawidłowe po następnym wywołaniu `iword` dla obiektu, gdy obiekt jest zmieniony przez wywołanie **basic_ios —::**[copyfmt —](../standard-library/basic-ios-class.md#copyfmt), lub gdy obiekt zostanie zniszczony.

Jeśli *idx* jest ujemne lub jeżeli unikatowy magazyn jest niedostępny dla elementu, funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)**(badbit)** i zwraca odwołanie, które nie muszą być unikatowe.

Aby uzyskać unikatowy indeks do użycia dla wszystkich obiektów typu `ios_base`, wywołaj [xalloc —](#xalloc).

### <a name="example"></a>Przykład

Zobacz [xalloc —](#xalloc) przykład sposobu użycia `iword`.

## <a name="openmode"></a>  ios_base::openmode

W tym artykule opisano sposób interakcji ze strumieniem.

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

Typ jest `bitmask type` , który opisuje obiekt, który może przechowywać tryb otwarcia kilka obiektów iostream. Flagi odrębne wartości (elementy) są następujące:

- `app`, aby starać się koniec strumienia przed każdym wstawiania.

- `ate`, do wyszukania na końcu strumienia, w chwili utworzenia jej kontrolowania obiektu.

- `binary`, można odczytać pliku jako strumienia binarnego, a nie jako strumienia tekstu.

- `in`, aby umożliwić wyodrębnianie ze strumienia.

- `out`, aby umożliwić wstawienie do strumienia.

- `trunc`, można usunąć zawartości istniejącego pliku, podczas jego kontrolowanie obiekt zostanie utworzony.

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

## <a name="op_eq"></a>  ios_base::operator =

Operator przypisania ios_base — obiektów.

```cpp
ios_base& operator=(const ios_base& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Obiekt typu `ios_base`.

### <a name="return-value"></a>Wartość zwracana

Obiekt, który jest przypisany do.

### <a name="remarks"></a>Uwagi

Operator kopiuje przechowywane informacje o formatowaniu, dzięki czemu nową kopię wszystkie tablice extensible. Następnie zwraca  **\*to**. Należy pamiętać, stos wywołań zwrotnych nie jest kopiowany.

Ten operator jest używana tylko przez klasy pochodne `ios_base`.

## <a name="precision"></a>  ios_base::Precision

Określa liczbę cyfr wyświetlanych w liczbę zmiennoprzecinkową.

```cpp
streamsize precision() const;
streamsize precision(streamsize _Prec);
```

### <a name="parameters"></a>Parametry

*_Prec*<br/>
Liczba cyfr znaczących, aby wyświetlić, lub liczbę cyfr po punkcie dziesiętnym w stałej cyfrowym.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca przechowywany [dokładność wyświetlania](../standard-library/ios-base-class.md). Drugi magazynów funkcja elementu członkowskiego *_Prec* precyzją wyświetlania i zwraca jego poprzedniej przechowywaną wartość.

### <a name="remarks"></a>Uwagi

Liczby zmiennoprzecinkowe są wyświetlane w stałym notacji z [stałej](../standard-library/ios-functions.md#fixed).

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

## <a name="pword"></a>  ios_base::pword

Przypisuje wartość do zapisania jako `pword`.

```cpp
void *& pword(int _Idx);
```

### <a name="parameters"></a>Parametry

*_Idx*<br/>
Indeks wartości do przechowywania jako `pword`.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do elementu _ *Idx* tablicy extensible elementami typu **void** wskaźnika. Wszystkie elementy są skutecznie obecne i początkowo przechowywane wskaźnika o wartości null. Zwracane odwołanie będzie nieprawidłowe po następnym wywołaniu `pword` dla obiektu, gdy obiekt jest zmieniony przez wywołanie **basic_ios —::**[copyfmt —](../standard-library/basic-ios-class.md#copyfmt), lub gdy obiekt zostanie zniszczony.

Jeśli _ *Idx* jest ujemna, lub jeśli unikatowy magazyn jest niedostępny dla elementu, funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)**(badbit)** i zwraca odwołanie, które nie muszą być unikatowe.

Aby uzyskać unikatowy indeks do użycia dla wszystkich obiektów typu `ios_base`, wywołaj [xalloc —](#xalloc).

### <a name="example"></a>Przykład

Zobacz [xalloc —](#xalloc) na przykład za pomocą `pword`.

## <a name="register_callback"></a>  ios_base::register_callback

Określa funkcję wywołania zwrotnego.

```cpp
void register_callback(
    event_callback pfn, int idx);
```

### <a name="parameters"></a>Parametry

*nazwy pfn*<br/>
Wskaźnik do funkcji wywołania zwrotnego.

*idx*<br/>
Liczba zdefiniowanych przez użytkownika.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wypycha pary `{pfn, idx}` na stosie wywołania zwrotnego przechowywanych [stos wywołań zwrotnych](../standard-library/ios-base-class.md). Gdy zdarzenie wywołania zwrotnego **weryfikacją** jest zgłaszany, funkcje są wywoływane, w odwrotnej kolejności z rejestru, przez wyrażenie `(*pfn)(ev, *this, idx)`.

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

## <a name="seekdir"></a> ios_base::seekdir

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

Typ jest typem wyliczanym, opisująca obiekt, które mogą być przechowywane jako argument do funkcji Członkowskich z kilku klas iostream tryb wyszukiwania. Wartości odrębnych flagi są następujące:

- `beg`, do wyszukania (alter bieżącego odczytu lub zapisu pozycji) względem początku sekwencji (tablicy, strumień lub plik).

- `cur`, do wyszukania względem bieżącej pozycji w sekwencji.

- `end`, do wyszukania względem końca sekwencji.

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

## <a name="setf"></a> ios_base::SETF

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

*_Maska*<br/>
Flagi, aby włączyć.

*_Unset*<br/>
Flagi, aby wyłączyć.

### <a name="return-value"></a>Wartość zwracana

Poprzednie flagi formatu

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego skutecznie wywołuje [flagi](#flags)(_ *maski* &#124; \_ *flagi*) (Ustaw wybrane usługi bits), a następnie zwraca poprzedniego flagi formatu. Funkcja drugiego członka skutecznie wywołuje **flagi**(\_ *maski* **& fmtfl, flagi & ~**`_Mask`) (Zastąp wybrany bitów pod maską) a następnie zwraca poprzedniego flagi formatu.

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

## <a name="sync_with_stdio"></a> ios_base::sync_with_stdio

Zapewnia, że iostream i operacje biblioteki wykonawczej C wystąpić w kolejności, w jakiej występują w kodzie źródłowym.

```cpp
static bool sync_with_stdio(
   bool _Sync = true
);
```

### <a name="parameters"></a>Parametry

*_Sync*<br/>
Czy wszystkie strumienie są zsynchronizowane z `stdio`.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienia dla tej funkcji.

### <a name="remarks"></a>Uwagi

Magazyny funkcja statycznej składowej `stdio` synchronizacji Flaga, która jest początkowo **true**. Podczas **true**, ta flaga gwarantuje, że operacje na tym samym pliku są poprawnie synchronizowane między [iostreams](../standard-library/iostreams-conventions.md) funkcje oraz tymi określonymi w standardowej biblioteki języka C++. W przeciwnym razie synchronizacja może lub nie ma gwarancji, ale można poprawić wydajność. Magazyny funkcji *_Sync* w `stdio` synchronizacji flagę i zwraca jego poprzednią wartość przechowywanych. Można też wywołać niezawodnie tylko przed wykonaniem jakichkolwiek działań na standardowych strumieni.

## <a name="unsetf"></a> ios_base::unsetf

Powoduje, że określone flagi były wyłączone.

```cpp
void unsetf(
   fmtflags _Mask
);
```

### <a name="parameters"></a>Parametry

*_Maska*<br/>
Flagi, które chcesz wyłączyć.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego skutecznie wywołuje [flagi](#flags)(`~`*_maska* **& flagi**) (Wyczyść wybrane usługi bits).

### <a name="example"></a>Przykład

Zobacz [ios_base::setf](#setf) przykład użycia `unsetf`.

## <a name="width"></a> ios_base::Width

Ustawia długość strumienia wyjściowego.

```cpp
streamsize width( ) const;
streamsize width(
   streamsize _Wide
);
```

### <a name="parameters"></a>Parametry

*_Wide*<br/>
Żądany rozmiar strumienia wyjściowego.

### <a name="return-value"></a>Wartość zwracana

Bieżące ustawienie szerokości.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego Zwraca szerokość pola przechowywanych. Drugi magazynów funkcja elementu członkowskiego *_Wide* szerokość pola i zwraca jego poprzedniej przechowywaną wartość.

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

## <a name="xalloc"></a> ios_base::xalloc

Określa, czy zmienna jest częścią strumienia.

```cpp
static int xalloc( );
```

### <a name="return-value"></a>Wartość zwracana

Funkcja statycznej składowej zwraca przechowywaną wartość statyczne, które zwiększa przy każdym wywołaniu.

### <a name="remarks"></a>Uwagi

Użyj wartości zwracanej jako argumenty unikatowy indeks podczas wywoływania funkcji elementu członkowskiego [iword —](#iword) lub [pword —](#pword).

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

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>

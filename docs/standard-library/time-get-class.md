---
title: time_get — Klasa
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get
- locale/std::time_get::char_type
- locale/std::time_get::iter_type
- locale/std::time_get::date_order
- locale/std::time_get::do_date_order
- locale/std::time_get::do_get
- locale/std::time_get::do_get_date
- locale/std::time_get::do_get_monthname
- locale/std::time_get::do_get_time
- locale/std::time_get::do_get_weekday
- locale/std::time_get::do_get_year
- locale/std::time_get::get
- locale/std::time_get::get_date
- locale/std::time_get::get_monthname
- locale/std::time_get::get_time
- locale/std::time_get::get_weekday
- locale/std::time_get::get_year
helpviewer_keywords:
- std::time_get [C++]
- std::time_get [C++], char_type
- std::time_get [C++], iter_type
- std::time_get [C++], date_order
- std::time_get [C++], do_date_order
- std::time_get [C++], do_get
- std::time_get [C++], do_get_date
- std::time_get [C++], do_get_monthname
- std::time_get [C++], do_get_time
- std::time_get [C++], do_get_weekday
- std::time_get [C++], do_get_year
- std::time_get [C++], get
- std::time_get [C++], get_date
- std::time_get [C++], get_monthname
- std::time_get [C++], get_time
- std::time_get [C++], get_weekday
- std::time_get [C++], get_year
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
ms.openlocfilehash: 45eeb7bdf944682ca168b8bff01b42815cfa7f28
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460012"
---
# <a name="timeget-class"></a>time_get — Klasa

Klasa szablonu opisuje obiekt, który może obsłużyć jako zestaw reguł ustawień regionalnych w celu kontrolowania konwersji sekwencji `CharType` typów do wartości czasu.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ używany w programie do kodowania znaków.

*InputIterator*\
Iterator, z którego są odczytywane wartości czasu.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[time_get](#time_get)|Konstruktor dla obiektów typu `time_get`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wejściowych.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[date_order](#date_order)|Zwraca kolejność dat używaną przez zestaw reguł.|
|[do_date_order](#do_date_order)|Chroniona funkcja wirtualna elementu członkowskiego, wywoływana, aby zwrócić kolejność dat używaną przez zestaw reguł.|
|[do_get](#do_get)|Odczytuje i konwertuje dane znakowe na wartość czasu.|
|[do_get_date](#do_get_date)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako `x` datę wygenerowaną `strftime`przez specyfikator dla.|
|[do_get_monthname](#do_get_monthname)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę miesiąca.|
|[do_get_time](#do_get_time)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako `X` datę wygenerowaną `strftime`przez specyfikator dla.|
|[do_get_weekday](#do_get_weekday)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę dnia tygodnia.|
|[do_get_year](#do_get_year)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę roku.|
|[get](#get)|Odczytuje ze źródła danych znakowych i konwertuje te dane na czas, który jest przechowywany w strukturze czasu.|
|[get_date](#get_date)|Analizuje ciąg jako datę wygenerowaną przez `x` specyfikator dla elementu. `strftime`|
|[get_monthname](#get_monthname)|Analizuje ciąg jako nazwę miesiąca.|
|[get_time](#get_time)|Analizuje ciąg jako datę wygenerowaną przez `X` specyfikator dla elementu. `strftime`|
|[get_weekday](#get_weekday)|Analizuje ciąg jako nazwę dnia tygodnia.|
|[get_year](#get_year)|Analizuje ciąg jako nazwę roku.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="char_type"></a>time_get::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu CharType .

## <a name="date_order"></a>time_get::d ate_order

Zwraca kolejność dat używaną przez zestaw reguł.

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolejność dat używana przez zestaw reguł.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_date_order](#do_date_order).

### <a name="example"></a>Przykład

```cpp
// time_get_date_order.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
void po( char *p )
{
   locale loc( p );

   time_get <char>::dateorder order = use_facet <time_get <char> >( loc ).date_order ( );
   cout << loc.name( );
   switch (order){
      case time_base::dmy: cout << "(day, month, year)" << endl;
      break;
      case time_base::mdy: cout << "(month, day, year)" << endl;
      break;
      case time_base::ydm: cout << "(year, day, month)" << endl;
      break;
      case time_base::ymd: cout << "(year, month, day)"<< endl;
      break;
      case time_base::no_order: cout << "(no_order)"<< endl;
      break;
   }
}

int main( )
{
   po( "C" );
   po( "german" );
   po( "English_Britain" );
}
```

```Output
C(month, day, year)
German_Germany.1252(day, month, year)
English_United Kingdom.1252(day, month, year)
```

## <a name="do_date_order"></a>  time_get::do_date_order

Chroniona funkcja wirtualna elementu członkowskiego, wywoływana, aby zwrócić kolejność dat używaną przez zestaw reguł.

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolejność dat używana przez zestaw reguł.

### <a name="remarks"></a>Uwagi

Wirtualna funkcja chroniona składowa zwraca wartość typu **time_base::d ateorder**, która opisuje kolejność, w jakiej składniki daty są dopasowane przez [do_get_date](#do_get_date). W tej implementacji wartość jest **time_base:: MDR**, odpowiadającą dacie formularza 2 grudnia 1979.

### <a name="example"></a>Przykład

Zobacz przykład dla [date_order](#date_order), który wywołuje `do_date_order`.

## <a name="do_get"></a>time_get::d o_get

Odczytuje i konwertuje dane znakowe na wartość czasu. Akceptuje jeden specyfikator konwersji i modyfikator.

```cpp
virtual iter_type
    do_get(
iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych, który wskazuje początek sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych, który wskazuje koniec sekwencji.

*iosbase*\
Obiekt strumienia.

*Państwu*\
Pole w iosbase, gdzie odpowiednie elementy maski bitowej są ustawione tak, aby wskazywały błędy.

*ptm*\
Wskaźnik do struktury czasu, w którym ma być przechowywany czas.

*FMT*\
Znak specyfikatora konwersji.

*Funkcja*\
Opcjonalny znak modyfikatora.

### <a name="return-value"></a>Wartość zwracana

Zwraca iterator, który wyznacza pierwszy nieprzekonwertowany element. Błędy konwersji są `ios_base::failbit` ustawiane `state` w i zwracane *jako pierwsze*.

### <a name="remarks"></a>Uwagi

Wirtualna funkcja członkowska konwertuje i pomija jeden lub więcej elementów wejściowych z zakresu [`first`, `last`), aby określić wartości przechowywane w `*pt`jednym lub większej liczbie elementów członkowskich. Błędy konwersji są `ios_base::failbit` ustawiane `state` w i zwracane *jako pierwsze*. W przeciwnym razie funkcja zwraca iterator wyznaczający pierwszy nieprzekonwertowany element.

Specyfikatory konwersji są następujące:

`'a'`lub `'A'` --zachowuje się tak samo jak [time_get:: get_weekday](#get_weekday).

`'b'`, `'B'`, lub `'h'` --zachowuje się tak samo jak [time_get:: get_monthname](#get_monthname).

`'c'`--zachowuje się tak samo jak `"%b %d %H : %M : %S %Y"`.

`'C'`--konwertuje pole wejściowe dziesiętne z zakresu [0, 99] na wartość `val` i zapisuje `val * 100 - 1900` w `pt-&tm_year`.

`'d'`lub `'e'` — konwertuje dziesiętne pole wejściowe z zakresu [1, 31] i zapisuje jego wartość w `pt-&tm_mday`.

`'D'`--zachowuje się tak samo jak `"%m / %d / %y"`.

`'H'`--konwertuje pole wejściowe dziesiętne w zakresie [0, 23] i zapisuje jego wartość w `pt-&tm_hour`.

`'I'`--konwertuje pole wejściowe dziesiętne z zakresu [0, 11] i zapisuje jego wartość w `pt-&tm_hour`.

`'j'`--konwertuje pole wejściowe dziesiętne z zakresu [1, 366] i zapisuje jego wartość w `pt-&tm_yday`.

`'m'`--Konwertuje dziesiętne pole wejściowe z zakresu [1, 12] na wartość `val` i zapisuje `val - 1` w i zapisuje jego wartość w `pt-&tm_mon`.

`'M'`--konwertuje pole wejściowe dziesiętne z zakresu [0, 59] i zapisuje jego wartość w `pt-&tm_min`.

`'n'`lub `'t'` --zachowuje się tak samo jak `" "`.

`'p'`--Konwertuje wartość "AM" lub "am" na zero, a "PM" lub "PM" do 12 i dodaje ją `pt-&tm_hour`do.

`'r'`--zachowuje się tak samo jak `"%I : %M : %S %p"`.

`'R'`--zachowuje się tak samo jak `"%H %M"`.

`'S'`--konwertuje pole wejściowe dziesiętne z zakresu [0, 59] i zapisuje jego wartość w `pt-&tm_sec`.

`'T'`lub `'X'` --zachowuje się tak samo jak `"%H : %M : S"`.

`'U'`--konwertuje pole wejściowe dziesiętne z zakresu [0, 53] i zapisuje jego wartość w `pt-&tm_yday`.

`'w'`--konwertuje pole wejściowe dziesiętne w zakresie [0, 6] i zapisuje jego wartość w `pt-&tm_wday`.

`'W'`--konwertuje pole wejściowe dziesiętne z zakresu [0, 53] i zapisuje jego wartość w `pt-&tm_yday`.

`'x'`--zachowuje się tak samo jak `"%d / %m / %y"`.

`'y'`--konwertuje pole wejściowe dziesiętne z zakresu [0, 99] na wartość `val` i zapisuje `val < 69  val + 100 : val` w `pt-&tm_year`.

`'Y'`--zachowuje się tak samo jak [time_get:: get_year](#get_year).

Wszystkie inne Specyfikatory konwersji są `ios_base::failbit` ustawiane w `state` i zwracają. W tej implementacji dowolny modyfikator nie ma wpływu.

## <a name="do_get_date"></a>time_get::d o_get_date

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako  datę wygenerowaną przez `strftime`specyfikator x dla.

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych odnoszący się do początku sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych odnoszący się do końca sekwencji do przekonwertowania.

*iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny. w przeciwnym razie jest to wymagane.

*Państwu*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się powodzeniem.

*ptm*\
Wskaźnik do lokalizacji, w której mają być przechowywane informacje o dacie.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu poza polem wejściowym.

### <a name="remarks"></a>Uwagi

Wirtualna funkcja chronionego elementu członkowskiego próbuje dopasować elementy sekwencyjne zaczynające się od `first`pierwszej `last`w sekwencji [,), dopóki nie rozpoznano kompletnego, niepustego pola wejściowego daty. Jeśli to się powiedzie, konwertuje to pole na jego równoważną wartość jako składniki **TM:\_: TM Mon**, **TM:\_: TM Day**, **TM::\_TM Year**i zapisuje wyniki w `ptm->tm_mon`, `ptm->tm_day`, i `ptm->tm_year`odpowiednio. Zwraca iterator wyznaczający pierwszy element poza pole danych wejściowych daty. W przeciwnym razie funkcje są `iosbase::failbit` ustawiane w *stanie*. Zwraca iterator wyznaczający pierwszy element poza dowolnym prefiksem prawidłowego pola wejściowego daty. W obu przypadkach, jeśli wartość zwracana jest równa *Last*, funkcja ustawia `ios_base::eofbit` w *stanie*.

Format pola danych wejściowych daty jest zależny od ustawień regionalnych. W przypadku domyślnych ustawień regionalnych pole daty wejścia ma postać MMM DD, rrrr, gdzie:

- MMM jest dopasowany przez wywołanie [get_monthname](#get_monthname), co miesiąc.

- DD jest sekwencją cyfr dziesiętnych, których odpowiadająca wartość liczbowa musi należeć do zakresu [1, 31], co oznacza dzień miesiąca.

- RRRR jest dopasowywane przez wywołanie [get_year](#get_year), co oznacza rok.

Spacje w postaci literałów i przecinki muszą być zgodne z odpowiednimi elementami w sekwencji wejściowej.

### <a name="example"></a>Przykład

Zobacz przykład dla [get_date](#get_date), który wywołuje `do_get_date`.

## <a name="do_get_monthname"></a>time_get::d o_get_monthname

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę miesiąca.

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych odnoszący się do początku sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych odnoszący się do końca sekwencji do przekonwertowania.

*iosbase*\
Przestrzeń.

*Państwu*\
Parametr wyjściowy, który ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacja zakończyła się pomyślnie.

*ptm*\
Wskaźnik do lokalizacji, w której mają być przechowywane informacje o miesiącach.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu poza polem wejściowym.

### <a name="remarks"></a>Uwagi

Wirtualna chroniona funkcja członkowska próbuje dopasować elementy sekwencyjne zaczynające się od pierwszej `first`w `last`sekwencji [,), dopóki nie rozpoznano kompletnego, niepustego miesiąca pola wejściowego. Jeśli to się powiedzie, konwertuje to pole na jego równoważną wartość jako składnik **TM:\_: TM Mon**i zapisuje wynik w `ptm->tm_mon`. Zwraca iterator wyznaczający pierwszy element wykraczający poza pole danych wejściowych miesiąca. W przeciwnym razie funkcje są `ios_base::failbit` ustawiane w *stanie*. Zwraca iterator wyznaczający pierwszy element poza dowolnym prefiksem prawidłowego pola wejściowego miesiąca. W obu przypadkach, jeśli wartość zwracana jest równa *Last*, funkcja ustawia `ios_base::eofbit` w *stanie*.

Pole danych wejściowych miesiąca jest sekwencją, która jest zgodna z najdłuższym zestawem sekwencji specyficznych dla ustawień regionalnych, takich jak Jan, styczeń, luty, luty itd. Przekonwertowana wartość to liczba miesięcy od stycznia.

### <a name="example"></a>Przykład

Zobacz przykład dla [get_monthname](#get_monthname), który wywołuje `do_get_monthname`.

## <a name="do_get_time"></a>time_get::d o_get_time

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako  datę wygenerowaną przez `strftime`specyfikator X dla.

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych odnoszący się do początku sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych odnoszący się do końca sekwencji do przekonwertowania.

*iosbase*\
Przestrzeń.

*Państwu*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się powodzeniem.

*ptm*\
Wskaźnik do lokalizacji, w której mają być przechowywane informacje o dacie.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu poza polem wejściowym.

### <a name="remarks"></a>Uwagi

Wirtualna funkcja chronionego elementu członkowskiego próbuje dopasować elementy sekwencyjne zaczynające się od `first`pierwszej `last`w sekwencji [,), dopóki nie rozpoznano kompletnego, niepustego pola wejściowego czasu. Jeśli to się powiedzie, konwertuje to pole na jego równoważną wartość `tm::tm_hour`jako `tm::tm_min`składniki, `tm::tm_sec`, i, i przechowuje wyniki `ptm->tm_hour`w `ptm->tm_min`,, `ptm->tm_sec`i, odpowiednio. Zwraca iterator wyznaczający pierwszy element poza pole wejściowy czas. W przeciwnym razie funkcje są `ios_base::failbit` ustawiane w *stanie*. Zwraca iterator wyznaczający pierwszy element poza dowolnym prefiksem prawidłowego pola wejściowego czasu. W obu przypadkach, jeśli wartość zwracana jest równa *Last*, funkcja ustawia `ios_base::eofbit` w *stanie*.

W tej implementacji pole Input Time ma postać HH: MM: SS, gdzie:

- HH jest sekwencją cyfr dziesiętnych, których odpowiadająca wartość liczbowa musi należeć do zakresu [0, 24), co oznacza godzinę dnia.

- MM jest sekwencją cyfr dziesiętnych, których odpowiadająca wartość liczbowa musi znajdować się w zakresie [0, 60), co oznacza, że liczba minut przypada na godzinę.

- SS jest sekwencją cyfr dziesiętnych, których odpowiadająca wartość liczbowa musi należeć do zakresu [0, 60), co powoduje, że sekundy czas przypada na minutę.

Dwukropki w literałach muszą być zgodne z odpowiednimi elementami w sekwencji wejściowej.

### <a name="example"></a>Przykład

Zobacz przykład dla [get_time](#get_time), który wywołuje `do_get_time`.

## <a name="do_get_weekday"></a>time_get::d o_get_weekday

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę dnia tygodnia.

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych odnoszący się do początku sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych odnoszący się do końca sekwencji do przekonwertowania.

*iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny. w przeciwnym razie jest to wymagane.

*Państwu*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się powodzeniem.

*ptm*\
Wskaźnik do lokalizacji, do której mają być przechowywane informacje o dniu tygodnia.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu poza polem wejściowym.

### <a name="remarks"></a>Uwagi

Wirtualna chroniona funkcja członkowska próbuje dopasować elementy sekwencyjne  zaczynające się od pierwszej `first`w `last`sekwencji [,), dopóki nie rozpoznano kompletnego, niepustego pola wejściowego dnia tygodnia. Jeśli to się powiedzie, konwertuje to pole na jego równoważną wartość jako składnik **TM:\_: TM wDay**i zapisuje wynik w `ptm->tm_wday`. Zwraca iterator wyznaczający pierwszy element poza pole danych wejściowych dnia tygodnia. W przeciwnym razie funkcje są `ios_base::failbit` ustawiane w *stanie*. Zwraca iterator wyznaczający pierwszy element poza dowolnym prefiksem prawidłowego pola wejściowego dnia tygodnia. W obu przypadkach, jeśli wartość zwracana jest równa *Last*, funkcja ustawia `ios_base::eofbit` w *stanie*.

Pole danych wejściowych dnia tygodnia jest sekwencją, która jest zgodna z najdłuższym zestawem sekwencji specyficznych dla ustawień regionalnych, takich jak Sun, niedziela, PN, poniedziałek itd. Przekonwertowana wartość to liczba dni od niedzieli.

### <a name="example"></a>Przykład

Zobacz przykład dla [get_weekday](#get_weekday), który wywołuje `do_get_weekday`.

## <a name="do_get_year"></a>time_get::d o_get_year

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę roku.

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych odnoszący się do początku sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych odnoszący się do końca sekwencji do przekonwertowania.

*iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny. w przeciwnym razie jest to wymagane.

*Państwu*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się powodzeniem.

*ptm*\
Wskaźnik do lokalizacji, w której mają być przechowywane informacje o roku.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu poza polem wejściowym.

### <a name="remarks"></a>Uwagi

Wirtualna chroniona funkcja członkowska próbuje dopasować elementy sekwencyjne  zaczynające się od pierwszej `first`w `last`sekwencji [,), dopóki nie rozpoznano kompletnego, niepustego pola wejściowego roku. Jeśli to się powiedzie, konwertuje to pole na odpowiadającą mu wartość jako składnik **TM:\_: TM roku**i zapisuje wynik w `ptm->tm_year`. Zwraca iterator wyznaczający pierwszy element poza pole danych wejściowych roku. W przeciwnym razie funkcje są `ios_base::failbit` ustawiane w *stanie*. Zwraca iterator wyznaczający pierwszy element poza dowolnym prefiksem pola wejściowego w prawidłowym roku. W obu przypadkach, jeśli wartość zwracana jest równa *Last*, funkcja ustawia `ios_base::eofbit` w *stanie*.

Pole wejściowe Year jest sekwencją cyfr dziesiętnych, których odpowiadająca wartość liczbowa musi należeć do zakresu [1900, 2036). Wartość przechowywana jest wartością minus 1900. W tej implementacji wartości z zakresu [69, 136) reprezentują zakres lat [1969, 2036). Dozwolone są również wartości z zakresu [0, 69), ale mogą one reprezentować albo zakres lat [1900, 1969), albo [2000, 2069), w zależności od konkretnego środowiska tłumaczenia.

### <a name="example"></a>Przykład

Zobacz przykład dla [get_year](#get_year), który wywołuje `do_get_year`.

## <a name="get"></a>time_get:: Get

Odczytuje ze źródła danych znakowych i konwertuje te dane na czas, który jest przechowywany w strukturze czasu. Pierwsza funkcja akceptuje jeden specyfikator konwersji i modyfikator, drugi akceptuje kilka.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char_type* fmt_first,
    char_type* fmt_last) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych, który wskazuje, gdzie zaczyna się sekwencja konwersji.

*ostatniego*\
Iterator danych wejściowych, który wskazuje koniec sekwencji do przekonwertowania.

*iosbase*\
Strumień.

*Państwu*\
Odpowiednie elementy masek bitowych są ustawiane dla stanu strumienia, aby wskazywały błędy.

*ptm*\
Wskaźnik na strukturę czasu, w której ma być przechowywany czas.

*FMT*\
Znak specyfikatora konwersji.

*Funkcja*\
Opcjonalny znak modyfikatora.

*fmt_first*\
Wskazuje, gdzie rozpoczyna się dyrektywa format.

*fmt_last*\
Wskazuje koniec dyrektyw formatu.

### <a name="return-value"></a>Wartość zwracana

Zwraca iterator do pierwszego znaku po danych, które zostały użyte do przypisania struktury `*ptm`czasu.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego `do_get(first, last, iosbase, state, ptm, fmt, mod)`zwraca.

Druga funkcja elementu członkowskiego `do_get` wywołuje kontrolę w formacie rozdzielonym przez. `[fmt_first, fmt_last)` Traktuje format jako sekwencję pól, z których każdy określa konwersję zero lub więcej elementów wejściowych rozdzielanych przez `[first, last)`. Zwraca iterator wyznaczający pierwszy nieprzekonwertowany element. Istnieją trzy rodzaje pól:

Procent (%) w formacie, po którym następuje opcjonalny modyfikator *mod* w zestawie [EOQ #], po którym następuje specyfikator konwersji *FMT*, zastępuje *najpierw* wartość zwróconą przez `do_get(first, last, iosbase, state, ptm, fmt, mod)`. Zestaw `ios_base::failbit` błędów konwersji w *stanie* i zwraca wartość.

Element odstępu w formacie powoduje pominięcie ostatnich zero lub więcej elementów odstępów wejściowych.

Każdy inny element w formacie musi pasować do następnego elementu wejściowego, który jest pomijany. Zestawy `ios_base::failbit` błędów dopasowania w *stanie* i Returns.

## <a name="get_date"></a>time_get::get_date

Analizuje ciąg jako datę wygenerowaną przez specyfikator *x* dla `strftime`.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych odnoszący się do początku sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych odnoszący się do końca sekwencji do przekonwertowania.

*iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny. w przeciwnym razie jest to wymagane.

*Państwu*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się powodzeniem.

*ptm*\
Wskaźnik do lokalizacji, w której mają być przechowywane informacje o dacie.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu poza polem wejściowym.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_get_date](#do_get_date)(`first` `last` `iosbase` `state`,,,, ).`ptm`

Należy pamiętać, że miesiące są liczone od 0 do 11.

### <a name="example"></a>Przykład

```cpp
// time_get_get_date.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset(&t, 0, sizeof(struct tm));

   pszGetF << "July 4, 2000";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get<char> >
   (loc).get_date(basic_istream<char>::_Iter(pszGetF.rdbuf( ) ),
            basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if ( st & ios_base::failbit )
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(July 4, 2000) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 4
tm_mon: 6
tm_year: 100
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="get_monthname"></a>time_get::get_monthname

Analizuje ciąg jako nazwę miesiąca.

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych odnoszący się do początku sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych odnoszący się do końca sekwencji do przekonwertowania.

*iosbase*\
Przestrzeń.

*Państwu*\
Parametr wyjściowy, który ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacja zakończyła się pomyślnie.

*ptm*\
Wskaźnik do lokalizacji, w której mają być przechowywane informacje o miesiącach.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu poza polem wejściowym.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_get_monthname](#do_get_monthname)(`first` `last` `iosbase` `state`,,,, ).`ptm`

### <a name="example"></a>Przykład

```cpp
// time_get_get_monthname.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "juillet";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get <char> >
   (loc).get_monthname(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
              basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(juillet) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 0
tm_mon: 6
tm_year: 0
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="get_time"></a>time_get::get_time

Analizuje ciąg jako datę wygenerowaną przez specyfikator *X* dla `strftime`.

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych odnoszący się do początku sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych odnoszący się do końca sekwencji do przekonwertowania.

*iosbase*\
Przestrzeń.

*Państwu*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się powodzeniem.

*ptm*\
Wskaźnik do lokalizacji, w której mają być przechowywane informacje o dacie.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu poza polem wejściowym.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_get_time](#do_get_time)(`first` `last` `iosbase` `state`,,,, ).`ptm`

### <a name="example"></a>Przykład

```cpp
// time_get_get_time.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "11:13:20";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get <char> >
      (loc).get_time(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << endl;
}
```

```Output
time_get::get_time(11:13:20) =
tm_sec: 20
tm_min: 13
tm_hour: 11
```

## <a name="get_weekday"></a>time_get::get_weekday

Analizuje ciąg jako nazwę dnia tygodnia.

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych odnoszący się do początku sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych odnoszący się do końca sekwencji do przekonwertowania.

*iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny. w przeciwnym razie jest to wymagane.

*Państwu*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się powodzeniem.

*ptm*\
Wskaźnik do lokalizacji, do której mają być przechowywane informacje o dniu tygodnia.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu poza polem wejściowym.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_get_weekday](#do_get_weekday)(`first` `last` `iosbase` `state`,,,, ).`ptm`

### <a name="example"></a>Przykład

```cpp
// time_get_get_weekday.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "mercredi";
   pszGetF.imbue(loc);
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_weekday(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_wday: " << t.tm_wday
      << endl;
}
```

```Output
time_get::get_time(mercredi) =
tm_wday: 3
```

## <a name="get_year"></a>time_get::get_year

Analizuje ciąg jako nazwę roku.

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych odnoszący się do początku sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych odnoszący się do końca sekwencji do przekonwertowania.

*iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny. w przeciwnym razie jest to wymagane.

*Państwu*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się powodzeniem.

*ptm*\
Wskaźnik do lokalizacji, w której mają być przechowywane informacje o roku.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu poza polem wejściowym.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_get_year](#do_get_year)(`first` `last` `iosbase` `state`,,,, ).`ptm`

### <a name="example"></a>Przykład

```cpp
// time_get_get_year.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "1928";

   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_year(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_year: " << t.tm_year
      << endl;
}
```

```Output
time_get::get_year(1928) =
tm_year: 28
```

## <a name="iter_type"></a>time_get::iter_type

Typ, który opisuje iterator danych wejściowych.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **InputIterator**.

## <a name="time_get"></a>time_get::time_get

Konstruktor dla obiektów typu `time_get`.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

*System*\
Wartość całkowita służąca do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *ReFS* i ich znaczenie są następujące:

- 0: Okres istnienia obiektu jest zarządzany przez elementy lokalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- \> 1: Te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój obiekt podstawowy przy użyciu **ustawień regionalnych::** [facet](../standard-library/locale-class.md#facet_class)(`refs`).

## <a name="see-also"></a>Zobacz także

[\<locale>](../standard-library/locale.md)\
[Klasa time_base](../standard-library/time-base-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

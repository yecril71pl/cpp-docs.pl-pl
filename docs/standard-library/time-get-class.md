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
ms.openlocfilehash: 9aebdaffc8bf3754bdbda08247f72ae08475711f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368035"
---
# <a name="time_get-class"></a>time_get — Klasa

Szablon klasy opisuje obiekt, który może służyć jako aspekt ustawień regionalnych `CharType` do kontrolowania konwersji sekwencji typu do wartości czasu.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ używany w programie do kodowania znaków.

*InputIterator*\
Iterator, z którego są odczytywane wartości czasu.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[time_get](#time_get)|Konstruktor obiektów typu `time_get`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wejściowych.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[date_order](#date_order)|Zwraca kolejność dat używaną przez zestaw reguł.|
|[do_date_order](#do_date_order)|Chroniona funkcja wirtualna elementu członkowskiego, wywoływana, aby zwrócić kolejność dat używaną przez zestaw reguł.|
|[do_get](#do_get)|Odczytuje i konwertuje dane znakowe na wartość czasu.|
|[do_get_date](#do_get_date)|Chroniona funkcja wirtualnego elementu członkowskiego, która jest wywoływana do `x` analizowania `strftime`ciągu jako daty wyprodukowanej przez specyfikator dla .|
|[do_get_monthname](#do_get_monthname)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę miesiąca.|
|[do_get_time](#do_get_time)|Chroniona funkcja wirtualnego elementu członkowskiego, która jest wywoływana do `X` analizowania `strftime`ciągu jako daty wyprodukowanej przez specyfikator dla .|
|[do_get_weekday](#do_get_weekday)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę dnia tygodnia.|
|[do_get_year](#do_get_year)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę roku.|
|[get](#get)|Odczytuje ze źródła danych znakowych i konwertuje te dane na czas, który jest przechowywany w strukturze czasu.|
|[get_date](#get_date)|Analizuje ciąg jako datę wyprodukowaną `x` przez specyfikator dla `strftime`.|
|[get_monthname](#get_monthname)|Analizuje ciąg jako nazwę miesiąca.|
|[get_time](#get_time)|Analizuje ciąg jako datę wyprodukowaną `X` przez specyfikator dla `strftime`.|
|[get_weekday](#get_weekday)|Analizuje ciąg jako nazwę dnia tygodnia.|
|[get_year](#get_year)|Analizuje ciąg jako nazwę roku.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="time_getchar_type"></a><a name="char_type"></a>time_get::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

## <a name="time_getdate_order"></a><a name="date_order"></a>time_get::date_order

Zwraca kolejność dat używaną przez zestaw reguł.

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolejność dat używana przez aspekt.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_date_order](#do_date_order).

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

## <a name="time_getdo_date_order"></a><a name="do_date_order"></a>time_get::do_date_order

Chroniona funkcja wirtualna elementu członkowskiego, wywoływana, aby zwrócić kolejność dat używaną przez zestaw reguł.

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolejność dat używana przez aspekt.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnego chronionego elementu członkowskiego zwraca wartość typu **time_base::dateorder**, która opisuje kolejność, w jakiej składniki daty są dopasowywać [do_get_date](#do_get_date). W tej implementacji wartość jest **time_base::mdy**, odpowiadająca datam formularza 2 grudnia 1979.

### <a name="example"></a>Przykład

Zobacz przykład [date_order](#date_order), który `do_date_order`wywołuje .

## <a name="time_getdo_get"></a><a name="do_get"></a>time_get::do_get

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

*Pierwszym*\
Iterator input, który wskazuje początek sekwencji do konwersji.

*Ostatnio*\
Iterator input, który wskazuje koniec sekwencji.

*baza iosbase*\
Obiekt strumienia.

*Państwa*\
Pole w bazie iosbase, w którym ustawione są odpowiednie elementy maski bitowej, aby wskazać błędy.

*Ptm*\
Wskaźnik do struktury czasu, w której ma być przechowywany czas.

*Fmt*\
Znak specyfikatora konwersji.

*Mod*\
Opcjonalny znak modyfikatora.

### <a name="return-value"></a>Wartość zwracana

Zwraca iterator, który wyznacza pierwszy nieprzekonwertowany element. Błąd konwersji `ios_base::failbit` `state` ustawia się i zwraca *jako pierwszy*.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnego elementu członkowskiego konwertuje i pomija jeden`first` `last`lub więcej elementów wejściowych w `*pt`zakresie [ , ), aby określić wartości przechowywane w jednym lub więcej elementach członkowskich programu . Błąd konwersji `ios_base::failbit` `state` ustawia się i zwraca *jako pierwszy*. W przeciwnym razie funkcja zwraca iterator wyznaczający pierwszy nieprzekonwertowany element.

Specyfikatory konwersji to:

`'a'`lub `'A'` -- zachowuje się tak samo jak [time_get::get_weekday](#get_weekday).

`'b'`, `'B'`lub `'h'` -- zachowuje się tak samo jak [time_get::get_monthname](#get_monthname).

`'c'`-- zachowuje się `"%b %d %H : %M : %S %Y"`tak samo jak .

`'C'`-- konwertuje pole wejściowe dziesiętne w zakresie [0, `val` 99] na wartość i przechowuje `val * 100 - 1900` w `pt-&tm_year`.

`'d'`lub `'e'` -- konwertuje pole wejściowe dziesiętne w zakresie [1, `pt-&tm_mday`31] i przechowuje jego wartość w .

`'D'`-- zachowuje się `"%m / %d / %y"`tak samo jak .

`'H'`-- konwertuje pole wejściowe dziesiętne w zakresie [0, 23] i przechowuje jego wartość w `pt-&tm_hour`.

`'I'`-- konwertuje pole wejściowe dziesiętne w zakresie [0, 11] i przechowuje jego wartość w `pt-&tm_hour`.

`'j'`-- konwertuje pole wejściowe dziesiętne w zakresie [1, 366] i przechowuje jego wartość w `pt-&tm_yday`.

`'m'`-- konwertuje pole wejściowe dziesiętne w zakresie [1, `val` 12] na wartość i przechowuje `val - 1` w i przechowuje jego wartość w `pt-&tm_mon`.

`'M'`-- konwertuje pole wejściowe dziesiętne w zakresie [0, 59] i przechowuje jego wartość w `pt-&tm_min`.

`'n'`lub `'t'` -- zachowuje się `" "`tak samo jak .

`'p'`-- konwertuje "AM" lub "am" na zero i "PM" lub "PM" na 12 i dodaje tę wartość do `pt-&tm_hour`.

`'r'`-- zachowuje się `"%I : %M : %S %p"`tak samo jak .

`'R'`-- zachowuje się `"%H %M"`tak samo jak .

`'S'`-- konwertuje pole wejściowe dziesiętne w zakresie [0, 59] i przechowuje jego wartość w `pt-&tm_sec`.

`'T'`lub `'X'` -- zachowuje się `"%H : %M : S"`tak samo jak .

`'U'`-- konwertuje pole wejściowe dziesiętne w zakresie [0, 53] i przechowuje jego wartość w `pt-&tm_yday`.

`'w'`-- konwertuje pole wejściowe dziesiętne w zakresie [0, `pt-&tm_wday`6] i przechowuje jego wartość w .

`'W'`-- konwertuje pole wejściowe dziesiętne w zakresie [0, 53] i przechowuje jego wartość w `pt-&tm_yday`.

`'x'`-- zachowuje się `"%d / %m / %y"`tak samo jak .

`'y'`-- konwertuje pole wejściowe dziesiętne w zakresie [0, `val` 99] na wartość i przechowuje `val < 69  val + 100 : val` w `pt-&tm_year`.

`'Y'`-- zachowuje się tak samo jak [time_get::get_year](#get_year).

Każdy inny specyfikator `ios_base::failbit` `state` konwersji ustawia i zwraca. W tej implementacji każdy modyfikator nie ma wpływu.

## <a name="time_getdo_get_date"></a><a name="do_get_date"></a>time_get::do_get_date

Chroniona funkcja wirtualnego elementu członkowskiego, która jest wywoływana do analizowania `strftime`ciągu jako daty wyprodukowanej przez *specyfikator x* dla .

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Iterator wejściowy adresowania początku sekwencji do konwersji.

*Ostatnio*\
Iterator wprowadzania adresowania koniec sekwencji do konwersji.

*baza iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny; w przeciwnym razie jest to wymagane.

*Państwa*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się pomyślnie.

*Ptm*\
Wskaźnik do miejsca przechowywania informacji o dacie.

### <a name="return-value"></a>Wartość zwracana

Iterator wejściowy adresowania pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnego chronionego elementu członkowskiego próbuje dopasować kolejne elementy `first`rozpoczynające się od początku w sekwencji [ , `last`), dopóki nie rozpozna kompletne, niepusty pole wprowadzania daty. Jeśli to się powiedzie, przekonwertuje to pole na jego wartość równoważną jako składniki **tm::tm\_mon**, **\_tm::tm day**i **tm::tm\_year**i przechowuje wyniki odpowiednio w `ptm->tm_mon`, `ptm->tm_day`i `ptm->tm_year`, odpowiednio. Zwraca iterator wyznaczający pierwszy element poza polem wejściowym daty. W przeciwnym razie `iosbase::failbit` funkcja ustawia się w *stanie*. Zwraca iterator wyznaczający pierwszy element poza prefiksem pola wejściowego prawidłowej daty. W obu przypadkach, jeśli zwracana wartość jest `ios_base::eofbit` równa *ostatniej,* funkcja ustawia się w *stanie*.

Format pola wprowadzania danych daty jest zależny od ustawień regionalnych. W przypadku domyślnych ustawień regionalnych pole wprowadzania daty ma formularz MMM DD, YYYY, gdzie:

- MMM jest dopasowywał [się](#get_monthname)do get_monthname dzwoniąc, dając miesiąc.

- DD jest sekwencją cyfr dziesiętnych, których odpowiednia wartość liczbowa musi znajdować się w zakresie [1, 31], podając dzień miesiąca.

- YYYY jest dopasowywał [się](#get_year)do get_year, dając rok.

Spacja literałowa i przecinki muszą być zgodne z odpowiednimi elementami w sekwencji wejściowej.

### <a name="example"></a>Przykład

Zobacz przykład [get_date](#get_date), który wywołuje `do_get_date`.

## <a name="time_getdo_get_monthname"></a><a name="do_get_monthname"></a>time_get::do_get_monthname

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę miesiąca.

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Iterator wejściowy adresowania początku sekwencji do konwersji.

*Ostatnio*\
Iterator wprowadzania adresowania koniec sekwencji do konwersji.

*baza iosbase*\
Nieużywany.

*Państwa*\
Parametr wyjściowy, który ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się pomyślnie.

*Ptm*\
Wskaźnik do miejsca przechowywania informacji o miesiącu.

### <a name="return-value"></a>Wartość zwracana

Iterator wejściowy adresowania pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnego chronionego elementu członkowskiego próbuje dopasować kolejne elementy `first`rozpoczynające się od początku w sekwencji [ , `last`), dopóki nie rozpozna kompletne, niepusty miesiąc pola wejściowego. Jeśli to się powiedzie, przekonwertuje to pole na jego wartość równoważną `ptm->tm_mon`jako składnik **tm::tm\_mon**i przechowuje wynik w . Zwraca iterator wyznaczający pierwszy element poza polem wejściowym miesiąca. W przeciwnym razie `ios_base::failbit` funkcja ustawia się w *stanie*. Zwraca iterator wyznaczający pierwszy element poza prefiksem pola wejściowego prawidłowego miesiąca. W obu przypadkach, jeśli zwracana wartość jest `ios_base::eofbit` równa *ostatniej,* funkcja ustawia się w *stanie*.

Pole wejściowe miesiąca jest sekwencją, która odpowiada najdłuższemu zestawowi sekwencji specyficznych dla ustawień regionalnych, takich jak Jan, Styczeń, Luty, Luty i tak dalej. Przekonwertowana wartość to liczba miesięcy od stycznia.

### <a name="example"></a>Przykład

Zobacz przykład [get_monthname](#get_monthname), który wywołuje `do_get_monthname`.

## <a name="time_getdo_get_time"></a><a name="do_get_time"></a>time_get::do_get_time

Chroniona funkcja wirtualnego elementu członkowskiego, która jest wywoływana do *X* analizowania `strftime`ciągu jako daty wyprodukowanej przez specyfikator x dla .

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Iterator wejściowy adresowania początku sekwencji do konwersji.

*Ostatnio*\
Iterator wprowadzania adresowania koniec sekwencji do konwersji.

*baza iosbase*\
Nieużywany.

*Państwa*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się pomyślnie.

*Ptm*\
Wskaźnik do miejsca przechowywania informacji o dacie.

### <a name="return-value"></a>Wartość zwracana

Iterator wejściowy adresowania pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnego chronionego elementu członkowskiego próbuje dopasować kolejne elementy `first`rozpoczynające się od początku w sekwencji [ , `last`), dopóki nie rozpozna kompletne, niepuchane pole wejściowe czasu. Jeśli to się powiedzie, konwertuje to `tm::tm_hour` `tm::tm_min`pole `tm::tm_sec`na jego wartość `ptm->tm_hour`równoważną jako składniki , i , i przechowuje wyniki w , `ptm->tm_min`i `ptm->tm_sec`, odpowiednio. Zwraca iterator wyznaczający pierwszy element poza polem wejściowym czasu. W przeciwnym razie `ios_base::failbit` funkcja ustawia się w *stanie*. Zwraca iterator wyznaczający pierwszy element poza prefiksem pola wprowadzania prawidłowego czasu. W obu przypadkach, jeśli zwracana wartość jest `ios_base::eofbit` równa *ostatniej,* funkcja ustawia się w *stanie*.

W tej implementacji pole danych wejściowych czasu ma formularz HH:MM:SS, gdzie:

- HH jest sekwencją cyfr dziesiętnych, których odpowiednia wartość liczbowa musi znajdować się w zakresie [0, 24), podając godzinę dnia.

- MM to sekwencja cyfr dziesiętnych, których odpowiednia wartość liczbowa musi znajdować się w zakresie [0, 60), co daje minuty po godzinie.

- SS jest sekwencją cyfr dziesiętnych, których odpowiednia wartość liczbowa musi znajdować się w zakresie [0, 60), co daje sekundy po minucie.

Dwukropki dosłowne muszą być zgodne z odpowiednimi elementami w sekwencji wejściowej.

### <a name="example"></a>Przykład

Zobacz przykład [get_time](#get_time), który wywołuje `do_get_time`.

## <a name="time_getdo_get_weekday"></a><a name="do_get_weekday"></a>time_get::do_get_weekday

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę dnia tygodnia.

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Iterator wejściowy adresowania początku sekwencji do konwersji.

*Ostatnio*\
Iterator wprowadzania adresowania koniec sekwencji do konwersji.

*baza iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny; w przeciwnym razie jest to wymagane.

*Państwa*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się pomyślnie.

*Ptm*\
Wskaźnik do miejsca przechowywania informacji o dniach tygodnia.

### <a name="return-value"></a>Wartość zwracana

Iterator wejściowy adresowania pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnego chronionego elementu członkowskiego próbuje dopasować kolejne elementy rozpoczynające się *od początku* w sekwencji [ `first`, `last`), dopóki nie rozpozna kompletne, niepusty pole wejściowe w dni powszednie. Jeśli to się powiedzie, przekonwertuje to pole na jego wartość równoważną jako `ptm->tm_wday`składnik **tm::tm\_wday**i przechowuje wynik w . Zwraca iterator wyznaczający pierwszy element poza polem wejściowym dnia tygodnia. W przeciwnym razie `ios_base::failbit` funkcja ustawia się w *stanie*. Zwraca iterator wyznaczający pierwszy element poza prefiksem prawidłowego pola wejściowego dnia tygodnia. W obu przypadkach, jeśli zwracana wartość jest `ios_base::eofbit` równa *ostatniej,* funkcja ustawia się w *stanie*.

Pole wejściowe dnia tygodnia jest sekwencją, która odpowiada najdłuższemu zestawowi sekwencji specyficznych dla ustawień regionalnych, takich jak Sun, Sunday, Pon, Monday i tak dalej. Przekonwertowana wartość to liczba dni od niedzieli.

### <a name="example"></a>Przykład

Zobacz przykład [get_weekday](#get_weekday), który wywołuje `do_get_weekday`.

## <a name="time_getdo_get_year"></a><a name="do_get_year"></a>time_get::do_get_year

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę roku.

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Iterator wejściowy adresowania początku sekwencji do konwersji.

*Ostatnio*\
Iterator wprowadzania adresowania koniec sekwencji do konwersji.

*baza iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny; w przeciwnym razie jest to wymagane.

*Państwa*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się pomyślnie.

*Ptm*\
Wskaźnik do miejsca przechowywania informacji o roku.

### <a name="return-value"></a>Wartość zwracana

Iterator wejściowy adresowania pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnego chronionego elementu członkowskiego próbuje dopasować kolejne elementy rozpoczynające się *od początku* w sekwencji [ `first`, `last`), dopóki nie rozpozna kompletne, niepusty rok pola wejściowego. Jeśli to się powiedzie, to pole zostanie przekonwertowane na jego wartość `ptm->tm_year`równoważną jako składnik **tm::tm\_year**i przechowuje wynik w . Zwraca iterator wyznaczający pierwszy element poza polem wejściowym roku. W przeciwnym razie `ios_base::failbit` funkcja ustawia się w *stanie*. Zwraca iterator wyznaczający pierwszy element poza prefiksem pola wejściowego prawidłowego roku. W obu przypadkach, jeśli zwracana wartość jest `ios_base::eofbit` równa *ostatniej,* funkcja ustawia się w *stanie*.

Pole wejściowe roku jest sekwencją cyfr dziesiętnych, których odpowiednia wartość liczbowa musi znajdować się w zakresie [1900, 2036). Przechowywana wartość jest tą wartością minus 1900. W tej implementacji wartości w zakresie [69, 136) reprezentują zakres lat [1969, 2036). Dopuszczalne są również wartości w zakresie [0, 69), ale mogą reprezentować zakres lat [1900, 1969) lub [2000, 2069), w zależności od konkretnego środowiska tłumaczenia.

### <a name="example"></a>Przykład

Zobacz przykład [get_year](#get_year), który wywołuje `do_get_year`.

## <a name="time_getget"></a><a name="get"></a>time_get::get

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

*Pierwszym*\
Iterator wejściowy, który wskazuje, gdzie rozpoczyna się sekwencja do konwersji.

*Ostatnio*\
Iterator wejściowy, który wskazuje koniec sekwencji, która ma zostać przekonwertowana.

*baza iosbase*\
Strumień.

*Państwa*\
Odpowiednie elementy maski bitowej są ustawione dla stanu strumienia, aby wskazać błędy.

*Ptm*\
Wskaźnik do struktury czasu, w której ma być przechowywany czas.

*Fmt*\
Znak specyfikatora konwersji.

*Mod*\
Opcjonalny znak modyfikatora.

*fmt_first*\
Wskazuje, gdzie zaczynają się dyrektywy formatu.

*fmt_last*\
Wskazuje na koniec dyrektyw formatu.

### <a name="return-value"></a>Wartość zwracana

Zwraca iterator do pierwszego znaku po danych, które zostały `*ptm`użyte do przypisania struktury czasu .

### <a name="remarks"></a>Uwagi

Zwraca pierwszą `do_get(first, last, iosbase, state, ptm, fmt, mod)`funkcję elementu członkowskiego .

Druga funkcja elementu `do_get` członkowskiego wywołuje pod kontrolą formatu rozdzielonego przez `[fmt_first, fmt_last)`program . Traktuje format jako sekwencję pól, z których każdy określa konwersję zero lub więcej `[first, last)`elementów wejściowych rozdzielonych przez . Zwraca iterator wyznaczający pierwszy nieprzekonwertowany element. Istnieją trzy rodzaje pól:

A procent (%) w formacie, a następnie opcjonalny *mod* modyfikator w zestawie [EOQ#], a następnie specyfikator konwersji *fmt*, zastępuje *najpierw* wartość zwróconą przez `do_get(first, last, iosbase, state, ptm, fmt, mod)`. Błąd konwersji `ios_base::failbit` ustawia się w *stanie* i zwraca.

Element odstępu w formacie pomija poza zero lub więcej wejściowych elementów odstępu.

Każdy inny element w formacie musi odpowiadać następnemu elementowi wejścinemu, który jest pomijany. Błąd dopasowania `ios_base::failbit` ustawia się w *stanie* i zwraca.

## <a name="time_getget_date"></a><a name="get_date"></a>time_get::get_date

Analizuje ciąg jako datę wyprodukowaną przez *specyfikator x* dla `strftime`.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Iterator wejściowy adresowania początku sekwencji do konwersji.

*Ostatnio*\
Iterator wprowadzania adresowania koniec sekwencji do konwersji.

*baza iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny; w przeciwnym razie jest to wymagane.

*Państwa*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się pomyślnie.

*Ptm*\
Wskaźnik do miejsca przechowywania informacji o dacie.

### <a name="return-value"></a>Wartość zwracana

Iterator wejściowy adresowania pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja elementu [do_get_date](#do_get_date)członkowskiego zwraca do_get_date`first` `last`( `iosbase` `state`, `ptm`, , , .

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

## <a name="time_getget_monthname"></a><a name="get_monthname"></a>time_get::get_monthname

Analizuje ciąg jako nazwę miesiąca.

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Iterator wejściowy adresowania początku sekwencji do konwersji.

*Ostatnio*\
Iterator wprowadzania adresowania koniec sekwencji do konwersji.

*baza iosbase*\
Nieużywany.

*Państwa*\
Parametr wyjściowy, który ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się pomyślnie.

*Ptm*\
Wskaźnik do miejsca przechowywania informacji o miesiącu.

### <a name="return-value"></a>Wartość zwracana

Iterator wejściowy adresowania pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja elementu [do_get_monthname](#do_get_monthname)członkowskiego zwraca do_get_monthname`first` `last`( `iosbase` `state`, `ptm`, , , .

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

## <a name="time_getget_time"></a><a name="get_time"></a>time_get::get_time

Analizuje ciąg jako datę wyprodukowaną *X* przez specyfikator `strftime`X dla .

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Iterator wejściowy adresowania początku sekwencji do konwersji.

*Ostatnio*\
Iterator wprowadzania adresowania koniec sekwencji do konwersji.

*baza iosbase*\
Nieużywany.

*Państwa*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się pomyślnie.

*Ptm*\
Wskaźnik do miejsca przechowywania informacji o dacie.

### <a name="return-value"></a>Wartość zwracana

Iterator wejściowy adresowania pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja elementu [do_get_time](#do_get_time)członkowskiego zwraca do_get_time`first` `last`( `iosbase` `state`, `ptm`, , , .

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

## <a name="time_getget_weekday"></a><a name="get_weekday"></a>time_get::get_weekday

Analizuje ciąg jako nazwę dnia tygodnia.

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Iterator wejściowy adresowania początku sekwencji do konwersji.

*Ostatnio*\
Iterator wprowadzania adresowania koniec sekwencji do konwersji.

*baza iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny; w przeciwnym razie jest to wymagane.

*Państwa*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się pomyślnie.

*Ptm*\
Wskaźnik do miejsca przechowywania informacji o dniach tygodnia.

### <a name="return-value"></a>Wartość zwracana

Iterator wejściowy adresowania pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja elementu [do_get_weekday](#do_get_weekday)członkowskiego zwraca do_get_weekday`first` `last`( `iosbase` `state`, `ptm`, , , .

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

## <a name="time_getget_year"></a><a name="get_year"></a>time_get::get_year

Analizuje ciąg jako nazwę roku.

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Iterator wejściowy adresowania początku sekwencji do konwersji.

*Ostatnio*\
Iterator wprowadzania adresowania koniec sekwencji do konwersji.

*baza iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny; w przeciwnym razie jest to wymagane.

*Państwa*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się pomyślnie.

*Ptm*\
Wskaźnik do miejsca przechowywania informacji o roku.

### <a name="return-value"></a>Wartość zwracana

Iterator wejściowy adresowania pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja elementu [do_get_year](#do_get_year)członkowskiego zwraca do_get_year`first` `last`( `iosbase` `state`, `ptm`, , , .

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

## <a name="time_getiter_type"></a><a name="iter_type"></a>time_get::iter_type

Typ, który opisuje iterator danych wejściowych.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru **szablonu InputIterator**.

## <a name="time_gettime_get"></a><a name="time_get"></a>time_get::time_get

Konstruktor obiektów typu `time_get`.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

*Bibl*\
Wartość całkowita używana do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *refs* i ich znaczenie to:

- 0: Okres istnienia obiektu jest zarządzany przez ustawienia regionalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: Te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój obiekt bazowy`refs`za pomocą **ustawień regionalnych::**[aspekt](../standard-library/locale-class.md#facet_class)( ).

## <a name="see-also"></a>Zobacz też

[\<>ustawień regionalnych](../standard-library/locale.md)\
[Klasa time_base](../standard-library/time-base-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

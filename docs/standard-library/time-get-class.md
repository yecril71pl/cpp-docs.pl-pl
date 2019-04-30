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
ms.openlocfilehash: df5a6da3995b1485585a3105ac027f19a27dc8eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412036"
---
# <a name="timeget-class"></a>time_get — Klasa

Klasa szablonu opisuje obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu `CharType` na wartości czasu.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ używany w programie do kodowania znaków.

*InputIterator*<br/>
Iterator, z którego są odczytywane wartości czasu.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba dostępu do jego przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikator.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[time_get](#time_get)|Konstruktor dla obiektów typu `time_get`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wejściowych.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[date_order](#date_order)|Zwraca kolejność dat używaną przez zestaw reguł.|
|[do_date_order](#do_date_order)|Chroniona funkcja wirtualna elementu członkowskiego, wywoływana, aby zwrócić kolejność dat używaną przez zestaw reguł.|
|[do_get](#do_get)|Odczytuje i konwertuje dane znakowe na wartość czasu.|
|[do_get_date](#do_get_date)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako datę produkowaną przez `x` specyfikatorem `strftime`.|
|[do_get_monthname](#do_get_monthname)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę miesiąca.|
|[do_get_time](#do_get_time)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako datę produkowaną przez `X` specyfikatorem `strftime`.|
|[do_get_weekday](#do_get_weekday)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę dnia tygodnia.|
|[do_get_year](#do_get_year)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę roku.|
|[get](#get)|Odczytuje ze źródła danych znakowych i konwertuje te dane na czas, który jest przechowywany w strukturze czasu.|
|[get_date](#get_date)|Analizuje ciąg jako datę produkowaną przez `x` specyfikatorem `strftime`.|
|[get_monthname](#get_monthname)|Analizuje ciąg jako nazwę miesiąca.|
|[get_time](#get_time)|Analizuje ciąg jako datę produkowaną przez `X` specyfikatorem `strftime`.|
|[get_weekday](#get_weekday)|Analizuje ciąg jako nazwę dnia tygodnia.|
|[get_year](#get_year)|Analizuje ciąg jako nazwę roku.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="char_type"></a>  time_get::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **CharType**.

## <a name="date_order"></a>  time_get::date_order

Zwraca kolejność dat używaną przez zestaw reguł.

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolejność dat używaną przez zestaw reguł.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_date_order —](#do_date_order).

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

Kolejność dat używaną przez zestaw reguł.

### <a name="remarks"></a>Uwagi

Funkcja wirtualna elementu członkowskiego chronionego zwraca wartość typu **time_base::dateorder**, która opisuje kolejność, w których data składniki są dopasowane przez [do_get_date —](#do_get_date). W tej implementacji wartość **time_base::mdy**, odpowiadające daty w postaci 2 grudnia 1979.

### <a name="example"></a>Przykład

Zobacz przykład [date_order —](#date_order), która wywołuje metodę `do_date_order`.

## <a name="do_get"></a>  time_get::do_get

Odczytuje i konwertuje dane znakowe na wartość czasu. Akceptuje specyfikatora konwersji jednego i modyfikator.

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

*pierwszy*<br/>
Iterator danych wejściowych, który wskazuje początek sekwencji do przekonwertowania.

*last*<br/>
Iterator danych wejściowych, który wskazuje na końcu sekwencji.

*iosbase*<br/>
Obiekt strumienia.

*state*<br/>
Pole w iosbase gdzie maski bitów odpowiednie elementy są ustawione do sygnalizowania błędów.

*ptm*<br/>
Wskaźnik do struktury czasu, gdy czas ma być przechowywany.

*fmt*<br/>
Znak specyfikatora konwersji.

*dzielenie modulo*<br/>
Opcjonalny modyfikator właściwy znak.

### <a name="return-value"></a>Wartość zwracana

Zwraca iterator opisujący pierwszy element nieprzekonwertowane. Błąd konwersji ustawia `ios_base::failbit` w `state` i zwraca *pierwszy*.

### <a name="remarks"></a>Uwagi

Funkcja wirtualna elementu członkowskiego konwertuje i pomija jeden lub więcej elementów w zakresie w danych wejściowych [`first`, `last`) można określić wartości przechowywane w jednej lub więcej członków `*pt`. Błąd konwersji ustawia `ios_base::failbit` w `state` i zwraca *pierwszy*. W przeciwnym razie funkcja zwraca iterator wyznaczanie pierwszy element nieprzekonwertowane.

Specyfikatory konwersji są następujące:

`'a'` lub `'A'` — działa tak samo jak [time_get::get_weekday](#get_weekday).

`'b'`, `'B'`, lub `'h'` — działa tak samo jak [time_get::get_monthname](#get_monthname).

`'c'` — działa tak samo jak `"%b %d %H : %M : %S %Y"`.

`'C'` — Konwertuje wartość dziesiętna pola wejściowego w zakresie [0, 99] `val` i przechowuje `val * 100 - 1900` w `pt-&tm_year`.

`'d'` lub `'e'` — konwertuje dziesiętna pola wejściowego z zakresu [1, 31] i przechowuje wartość w `pt-&tm_mday`.

`'D'` — działa tak samo jak `"%m / %d / %y"`.

`'H'` — Konwertuje wartość dziesiętna pola wejściowego w zakresie [0, 23], a następnie przechowuje wartość w `pt-&tm_hour`.

`'I'` — Konwertuje wartość dziesiętna pola wejściowego w zakresie [0, 11], a następnie przechowuje wartość w `pt-&tm_hour`.

`'j'` — Konwertuje wartość dziesiętna pola wejściowego z zakresu [1, 366], a następnie przechowuje wartość w `pt-&tm_yday`.

`'m'` — Konwertuje wartość dziesiętna pola wejściowego z zakresu [1, 12] `val` i przechowuje `val - 1` w i przechowuje wartość w `pt-&tm_mon`.

`'M'` — Konwertuje wartość dziesiętna pola wejściowego w zakresie [0, 59], a następnie przechowuje wartość w `pt-&tm_min`.

`'n'` lub `'t'` — działa tak samo jak `" "`.

`'p'` — Konwertuje "ciąg AM" lub "am" zero i "PM" lub "PM" 12 i dodaje tę wartość, aby `pt-&tm_hour`.

`'r'` — działa tak samo jak `"%I : %M : %S %p"`.

`'R'` — działa tak samo jak `"%H %M"`.

`'S'` — Konwertuje wartość dziesiętna pola wejściowego w zakresie [0, 59], a następnie przechowuje wartość w `pt-&tm_sec`.

`'T'` lub `'X'` — działa tak samo jak `"%H : %M : S"`.

`'U'` — Konwertuje wartość dziesiętna pola wejściowego w zakresie [0, 53], a następnie przechowuje wartość w `pt-&tm_yday`.

`'w'` — Konwertuje wartość dziesiętna pola wejściowego w zakresie [0, 6], a następnie przechowuje wartość w `pt-&tm_wday`.

`'W'` — Konwertuje wartość dziesiętna pola wejściowego w zakresie [0, 53], a następnie przechowuje wartość w `pt-&tm_yday`.

`'x'` — działa tak samo jak `"%d / %m / %y"`.

`'y'` — Konwertuje wartość dziesiętna pola wejściowego w zakresie [0, 99] `val` i przechowuje `val < 69  val + 100 : val` w `pt-&tm_year`.

`'Y'` — działa tak samo jak [time_get::get_year](#get_year).

Inne zestawy specyfikatora konwersji `ios_base::failbit` w `state` i zwraca. W tej implementacji wszelkich modyfikator nie ma znaczenia.

## <a name="do_get_date"></a>  time_get::do_get_date

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako datę produkowaną przez *x* specyfikatorem `strftime`.

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się na początku sekwencji, który ma zostać przekonwertowany.

*last*<br/>
Iterator danych wejściowych, odnoszący się koniec sekwencji, który ma zostać przekonwertowany.

*iosbase*<br/>
Flagi formatu, który po zestaw wskazuje, że symbol waluty jest opcjonalna. w przeciwnym razie jest ona wymagana.

*state*<br/>
Ustawia elementy odpowiedniej maski bitów dla stanu strumień zgodnie z tego, czy operacje zakończyło się pomyślnie.

*ptm*<br/>
Wskaźnik do której ma być przechowywane informacje o dacie.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych, odnoszący się do pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualna elementu członkowskiego chronionego próbuje dopasować kolejne elementy od początku sekwencji [ `first`, `last`), dopóki nie został rozpoznany kompletna, Data niepustych dane wejściowe pola. Jeśli operacja się powiedzie, konwertuje tego pola do jego równoważną wartość jako składniki **tm::tm\_mon**, **tm::tm\_dzień**, i **tm::tm\_roku** i zapisuje wyniki w parametrze `ptm->tm_mon`, `ptm->tm_day`, i `ptm->tm_year`, odpowiednio. Zwraca iterator, wyznaczanie pierwszego elementu poza pole wprowadzania daty. W przeciwnym razie funkcja ustawia `iosbase::failbit` w *stanu*. Zwraca iterator wyznaczanie pierwszego elementu poza dowolnego prefiksu pole wprowadzania prawidłowej daty. W obu przypadkach, jeśli wartość zwracana równa *ostatniego*, zestawy funkcji `ios_base::eofbit` w *stanu*.

Format pole wprowadzania daty jest zależne od ustawień regionalnych. Dla domyślnych ustawień regionalnych, pole wprowadzania daty ma postać MMM DD, rrrr, gdzie:

- MMM dorównuje wywoływania [get_monthname —](#get_monthname), dzięki czemu miesiąca.

- DD to sekwencja cyfr dziesiętnych, którego wartość liczbową odpowiedniego musi być z zakresu [1, 31] zapewniając dnia miesiąca.

- RRRR jest dopasowywany przez wywołanie metody [get_year —](#get_year), dzięki czemu roku.

Literał spacje i przecinki musi odpowiadać odpowiednie elementy w sekwencji wejściowych.

### <a name="example"></a>Przykład

Zobacz przykład [get_date —](#get_date), która wywołuje metodę `do_get_date`.

## <a name="do_get_monthname"></a>  time_get::do_get_monthname

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę miesiąca.

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się na początku sekwencji, który ma zostać przekonwertowany.

*last*<br/>
Iterator danych wejściowych, odnoszący się koniec sekwencji, który ma zostać przekonwertowany.

*iosbase*<br/>
Nieużywane.

*state*<br/>
Parametr wyjściowy, który ustawia elementy odpowiedniej maski bitów dla stanu strumień zgodnie z tego, czy operacje zakończyło się pomyślnie.

*ptm*<br/>
Wskaźnik do której informacje miesiąc ma być przechowywany.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych, odnoszący się do pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualna elementu członkowskiego chronionego próbuje dopasować kolejne elementy od początku sekwencji [ `first`, `last`), dopóki nie został rozpoznany kompletna, niepustych miesiąca dane wejściowe pola. Jeśli operacja się powiedzie, konwertuje to pole na jego równoważną wartość jako składnik **tm::tm\_mon**i zapisuje wynik w `ptm->tm_mon`. Zwraca iterator, wyznaczanie pierwszego elementu poza pole wejściowe miesiąca. W przeciwnym razie funkcja ustawia `ios_base::failbit` w *stanu*. Zwraca iterator wyznaczanie pierwszego elementu poza dowolnego prefiksu prawidłowy miesiąca pola wejściowego. W obu przypadkach, jeśli wartość zwracana równa *ostatniego*, zestawy funkcji `ios_base::eofbit` w *stanu*.

Pole wprowadzania miesiąca jest sekwencji która pasuje najdłuższy zestaw sekwencje specyficzne dla ustawień regionalnych, takich jak sty, stycznia, lutego lutego i tak dalej. Przekonwertowana wartości jest liczba miesięcy od stycznia.

### <a name="example"></a>Przykład

Zobacz przykład [get_monthname —](#get_monthname), która wywołuje metodę `do_get_monthname`.

## <a name="do_get_time"></a>  time_get::do_get_time

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako datę produkowaną przez *X* specyfikatorem `strftime`.

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się na początku sekwencji, który ma zostać przekonwertowany.

*last*<br/>
Iterator danych wejściowych, odnoszący się koniec sekwencji, który ma zostać przekonwertowany.

*iosbase*<br/>
Nieużywane.

*state*<br/>
Ustawia elementy odpowiedniej maski bitów dla stanu strumień zgodnie z tego, czy operacje zakończyło się pomyślnie.

*ptm*<br/>
Wskaźnik do której ma być przechowywane informacje o dacie.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych, odnoszący się do pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualna elementu członkowskiego chronionego próbuje dopasować kolejne elementy od początku sekwencji [ `first`, `last`), dopóki nie został rozpoznany kompletna, niepustych czas wejściowy pola. Jeśli operacja się powiedzie, konwertuje tego pola do jego równoważną wartość jako składniki `tm::tm_hour`, `tm::tm_min`, i `tm::tm_sec`i zapisuje wyniki w parametrze `ptm->tm_hour`, `ptm->tm_min`, i `ptm->tm_sec`, odpowiednio. Zwraca iterator, wyznaczanie pierwszego elementu poza pole wprowadzania godziny. W przeciwnym razie funkcja ustawia `ios_base::failbit` w *stanu*. Zwraca iterator wyznaczanie pierwszego elementu poza dowolnego prefiksu prawidłowy czas pola wejściowego. W obu przypadkach, jeśli wartość zwracana równa *ostatniego*, zestawy funkcji `ios_base::eofbit` w *stanu*.

W tej implementacji czasu pole wejściowe ma postać: mm: ss, gdzie:

- HH to sekwencja cyfr dziesiętnych, którego wartość liczbową odpowiedniego musi należeć do zakresu [0, 24), dzięki czemu godziny dnia.

- MM to sekwencja cyfr dziesiętnych, którego wartość liczbową odpowiedniego musi należeć do zakresu [0, 60), dzięki czemu minut po pełnej godzinie.

- SS to sekwencja cyfr dziesiętnych, którego wartość liczbową odpowiedniego musi należeć do zakresu [0, 60) sekund po pełnej minucie, zapewniając.

W dwukropki literału musi odpowiadać odpowiednie elementy w sekwencji wejściowych.

### <a name="example"></a>Przykład

Zobacz przykład [get_time —](#get_time), która wywołuje metodę `do_get_time`.

## <a name="do_get_weekday"></a>  time_get::do_get_weekday

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę dnia tygodnia.

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się na początku sekwencji, który ma zostać przekonwertowany.

*last*<br/>
Iterator danych wejściowych, odnoszący się koniec sekwencji, który ma zostać przekonwertowany.

*iosbase*<br/>
Flagi formatu, który po zestaw wskazuje, że symbol waluty jest opcjonalna. w przeciwnym razie jest ona wymagana.

*state*<br/>
Ustawia elementy odpowiedniej maski bitów dla stanu strumień zgodnie z tego, czy operacje zakończyło się pomyślnie.

*ptm*<br/>
Wskaźnik do której ma być przechowywany informacji dzień tygodnia.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych, odnoszący się do pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualna elementu członkowskiego chronionego próbuje dopasować elementów sekwencyjnego, rozpoczynając od *pierwszy* w sekwencji [ `first`, `last`), dopóki nie został rozpoznany kompletna, weekday niepustych dane wejściowe pola. Jeśli operacja się powiedzie, konwertuje to pole na jego równoważną wartość jako składnik **tm::tm\_tej notacji**i zapisuje wynik w `ptm->tm_wday`. Zwraca iterator, wyznaczanie pierwszego elementu poza pole wejściowe dzień tygodnia. W przeciwnym razie funkcja ustawia `ios_base::failbit` w *stanu*. Zwraca iterator, wyznaczanie pierwszego elementu poza dowolnego prefiksu, pola wejściowego nieprawidłowy dzień tygodnia. W obu przypadkach, jeśli wartość zwracana równa *ostatniego*, zestawy funkcji `ios_base::eofbit` w *stanu*.

Pole wprowadzania dnia tygodnia jest sekwencji która pasuje najdłuższy zestaw sekwencje specyficzne dla ustawień regionalnych, takich jak Sun, niedziela, Mon poniedziałek i tak dalej. Przekonwertowana wartość jest liczbą dni od niedzieli.

### <a name="example"></a>Przykład

Zobacz przykład [get_weekday —](#get_weekday), która wywołuje metodę `do_get_weekday`.

## <a name="do_get_year"></a>  time_get::do_get_year

Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę roku.

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się na początku sekwencji, który ma zostać przekonwertowany.

*last*<br/>
Iterator danych wejściowych, odnoszący się koniec sekwencji, który ma zostać przekonwertowany.

*iosbase*<br/>
Flagi formatu, który po zestaw wskazuje, że symbol waluty jest opcjonalna. w przeciwnym razie jest ona wymagana.

*state*<br/>
Ustawia elementy odpowiedniej maski bitów dla stanu strumień zgodnie z tego, czy operacje zakończyło się pomyślnie.

*ptm*<br/>
Wskaźnik do których informacji o roku ma być przechowywany.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych, odnoszący się do pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualna elementu członkowskiego chronionego próbuje dopasować elementów sekwencyjnego, rozpoczynając od *pierwszy* w sekwencji [ `first`, `last`), dopóki nie został rozpoznany kompletna, niepustych roku dane wejściowe pól. Jeśli operacja się powiedzie, konwertuje to pole na jego równoważną wartość jako składnik **tm::tm\_roku**i zapisuje wynik w `ptm->tm_year`. Zwraca iterator, wyznaczanie pierwszego elementu poza pole wejściowe roku. W przeciwnym razie funkcja ustawia `ios_base::failbit` w *stanu*. Zwraca iterator wyznaczanie pierwszego elementu poza dowolnego prefiksu prawidłowy rok pola wejściowego. W obu przypadkach, jeśli wartość zwracana równa *ostatniego*, zestawy funkcji `ios_base::eofbit` w *stanu*.

Pole wprowadzania roku jest sekwencją cyfr dziesiętnych, którego wartość liczbową odpowiedniego musi należeć do zakresu [1900, 2036). Wartość przechowywana jest ta wartość minus 1900. W tej implementacji wartości z zakresu [69, 136) reprezentują zakresu lat [1969, 2036). Wartości w zakresie [0, 69) także są dopuszczalne, ale może reprezentować zakresu lat [1900, 1969) lub [2000, 2069), w zależności od określonego środowiska translacji.

### <a name="example"></a>Przykład

Zobacz przykład [get_year —](#get_year), która wywołuje metodę `do_get_year`.

## <a name="get"></a>  time_get::Get

Odczytuje ze źródła danych znakowych i konwertuje te dane na czas, który jest przechowywany w strukturze czasu. Pierwsza funkcja akceptuje specyfikatora konwersji jednego i modyfikator, druga akceptuje kilka.

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

*pierwszy*<br/>
Iterator danych wejściowych, która wskazuje, gdzie rozpoczyna się sekwencja, który ma zostać przekonwertowany.

*last*<br/>
Iterator danych wejściowych, który wskazuje koniec sekwencji, który ma zostać przekonwertowany.

*iosbase*<br/>
Strumień.

*state*<br/>
Elementy odpowiedniej maski bitów są ustawiane dla stanu strumienia do sygnalizowania błędów.

*ptm*<br/>
Wskaźnik do struktury czasu, gdy czas ma być przechowywany.

*fmt*<br/>
Znak specyfikatora konwersji.

*dzielenie modulo*<br/>
Opcjonalny modyfikator właściwy znak.

*fmt_first*<br/>
Wskazuje gdzie rozpocząć dyrektywy formatu.

*fmt_last*<br/>
Wskazuje koniec dyrektywy formatu.

### <a name="return-value"></a>Wartość zwracana

Zwraca iterator do pierwszego znaku po danych, który został użyty do przypisywania strukturze czasu `*ptm`.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca `do_get(first, last, iosbase, state, ptm, fmt, mod)`.

Drugi wywołania funkcji elementu członkowskiego `do_get` pod kontrolą formatu rozdzielone `[fmt_first, fmt_last)`. Format traktuje jako sekwencja pól, z których każdy określa konwersji zero lub więcej elementów rozdzielonych w danych wejściowych `[first, last)`. Zwraca iterator wyznaczanie pierwszy element nieprzekonwertowane. Istnieją trzy rodzaje pola:

Procent (%) w formacie, następuje opcjonalny modyfikator właściwy *mod* w zestawie EOQ #, a następnie specyfikatora konwersji *fmt*, zastępuje *pierwszy* z wartością zwróconą przez `do_get(first, last, iosbase, state, ptm, fmt, mod)`. Błąd konwersji ustawia `ios_base::failbit` w *stanu* i zwraca.

Element białe znaki w formacie pomija zero lub więcej spacji elementów input.

Inny element, w formacie muszą być zgodne następnego elementu danych wejściowych jest pomijany. Niepowodzenie dopasowania ustawia `ios_base::failbit` w *stanu* i zwraca.

## <a name="get_date"></a>  time_get::get_date

Analizuje ciąg jako datę produkowaną przez *x* specyfikatorem `strftime`.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się na początku sekwencji, który ma zostać przekonwertowany.

*last*<br/>
Iterator danych wejściowych, odnoszący się koniec sekwencji, który ma zostać przekonwertowany.

*iosbase*<br/>
Flagi formatu, który po zestaw wskazuje, że symbol waluty jest opcjonalna. w przeciwnym razie jest ona wymagana.

*state*<br/>
Ustawia elementy odpowiedniej maski bitów dla stanu strumień zgodnie z tego, czy operacje zakończyło się pomyślnie.

*ptm*<br/>
Wskaźnik do której ma być przechowywane informacje o dacie.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych, odnoszący się do pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_get_date —](#do_get_date)(`first`, `last`, `iosbase`, `state`, `ptm`).

Należy pamiętać, że miesięcy są liczone od 0 do 11.

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

## <a name="get_monthname"></a>  time_get::get_monthname

Analizuje ciąg jako nazwę miesiąca.

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się na początku sekwencji, który ma zostać przekonwertowany.

*last*<br/>
Iterator danych wejściowych, odnoszący się koniec sekwencji, który ma zostać przekonwertowany.

*iosbase*<br/>
Nieużywane.

*state*<br/>
Parametr wyjściowy, który ustawia elementy odpowiedniej maski bitów dla stanu strumień zgodnie z tego, czy operacje zakończyło się pomyślnie.

*ptm*<br/>
Wskaźnik do której informacje miesiąc ma być przechowywany.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych, odnoszący się do pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_get_monthname —](#do_get_monthname)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="get_time"></a>  time_get::get_time

Analizuje ciąg jako datę produkowaną przez *X* specyfikatorem `strftime`.

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się na początku sekwencji, który ma zostać przekonwertowany.

*last*<br/>
Iterator danych wejściowych, odnoszący się koniec sekwencji, który ma zostać przekonwertowany.

*iosbase*<br/>
Nieużywane.

*state*<br/>
Ustawia elementy odpowiedniej maski bitów dla stanu strumień zgodnie z tego, czy operacje zakończyło się pomyślnie.

*ptm*<br/>
Wskaźnik do której ma być przechowywane informacje o dacie.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych, odnoszący się do pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_get_time —](#do_get_time)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="get_weekday"></a>  time_get::get_weekday

Analizuje ciąg jako nazwę dnia tygodnia.

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się na początku sekwencji, który ma zostać przekonwertowany.

*last*<br/>
Iterator danych wejściowych, odnoszący się koniec sekwencji, który ma zostać przekonwertowany.

*iosbase*<br/>
Flagi formatu, który po zestaw wskazuje, że symbol waluty jest opcjonalna. w przeciwnym razie jest ona wymagana.

*state*<br/>
Ustawia elementy odpowiedniej maski bitów dla stanu strumień zgodnie z tego, czy operacje zakończyło się pomyślnie.

*ptm*<br/>
Wskaźnik do której ma być przechowywany informacji dzień tygodnia.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych, odnoszący się do pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_get_weekday —](#do_get_weekday)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="get_year"></a>  time_get::get_year

Analizuje ciąg jako nazwę roku.

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się na początku sekwencji, który ma zostać przekonwertowany.

*last*<br/>
Iterator danych wejściowych, odnoszący się koniec sekwencji, który ma zostać przekonwertowany.

*iosbase*<br/>
Flagi formatu, który po zestaw wskazuje, że symbol waluty jest opcjonalna. w przeciwnym razie jest ona wymagana.

*state*<br/>
Ustawia elementy odpowiedniej maski bitów dla stanu strumień zgodnie z tego, czy operacje zakończyło się pomyślnie.

*ptm*<br/>
Wskaźnik do których informacji o roku ma być przechowywany.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych, odnoszący się do pierwszego elementu poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_get_year —](#do_get_year)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="iter_type"></a>  time_get::iter_type

Typ, który opisuje iterator danych wejściowych.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **InputIterator**.

## <a name="time_get"></a>  time_get::time_get

Konstruktor dla obiektów typu `time_get`.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

*System plików refs*<br/>
Wartość liczby całkowitej, można określić typ zarządzania pamięci dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *system plików refs* parametrów i ich znaczenie są:

- 0: Okres istnienia obiektu jest zarządzany przez ustawienia regionalne, zawierających go.

- 1: Okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: Te wartości nie są zdefiniowane.

Żadnych przykładów bezpośrednie są to tylko możliwe, ponieważ destruktor jest chroniony.

Konstruktor inicjuje jego podstawowego obiektu z **locale::**[aspekt](../standard-library/locale-class.md#facet_class)(`refs`).

## <a name="see-also"></a>Zobacz także

[\<locale>](../standard-library/locale.md)<br/>
[time_base, klasa](../standard-library/time-base-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

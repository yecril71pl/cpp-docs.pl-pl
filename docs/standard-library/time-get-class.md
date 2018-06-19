---
title: time_get — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c3db9edd974d111881b17b6f1a53c1b4ac3b336
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862851"
---
# <a name="timeget-class"></a>time_get — Klasa

Klasa szablonu opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do sterowania konwersje sekwencji typu `CharType` do wartości typu time.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Parametry

`CharType` Typ używany w programie do kodowania znaków.

`InputIterator` Iterator, z której są odczytywane wartości czasu.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba jej wartości przechowywanej dostępu są przechowywane w unikatową wartość dodatnią **identyfikator.**

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

|Funkcja członkowska|Opis|
|-|-|
|[date_order](#date_order)|Zwraca kolejność dat używaną przez zestaw reguł.|
|[do_date_order](#do_date_order)|Chroniona funkcja wirtualna elementu członkowskiego, wywoływana, aby zwrócić kolejność dat używaną przez zestaw reguł.|
|[do_get](#do_get)|Odczytuje i konwertuje dane znakowe na wartość czasu.|
|[do_get_date](#do_get_date)|A chronione wirtualnej funkcji członkowskiej wywoływaną, można przeanalizować ciągu jako data utworzonego przez `x` specyfikatora `strftime`.|
|[do_get_monthname](#do_get_monthname)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę miesiąca.|
|[do_get_time](#do_get_time)|A chronione wirtualnej funkcji członkowskiej wywoływaną, można przeanalizować ciągu jako data utworzonego przez `X` specyfikatora `strftime`.|
|[do_get_weekday](#do_get_weekday)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę dnia tygodnia.|
|[do_get_year](#do_get_year)|Chroniona funkcja wirtualna elementu członkowskiego, która jest wywoływana, aby przeanalizować ciąg jako nazwę roku.|
|[get](#get)|Odczytuje ze źródła danych znakowych i konwertuje te dane na czas, który jest przechowywany w strukturze czasu.|
|[get_date](#get_date)|Analizuje ciąg jako data utworzonego przez `x` specyfikatora `strftime`.|
|[get_monthname](#get_monthname)|Analizuje ciąg jako nazwę miesiąca.|
|[get_time](#get_time)|Analizuje ciąg jako data utworzonego przez `X` specyfikatora `strftime`.|
|[get_weekday](#get_weekday)|Analizuje ciąg jako nazwę dnia tygodnia.|
|[get_year](#get_year)|Analizuje ciąg jako nazwę roku.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** Standard

## <a name="char_type"></a>  time_get::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

## <a name="date_order"></a>  time_get::date_order

Zwraca kolejność dat używaną przez zestaw reguł.

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolejność daty używane przez zestaw reguł.

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

Kolejność daty używane przez zestaw reguł.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnej chroniony element członkowski zwraca wartość typu **time_base::dateorder**, która opisuje kolejność daty, które składniki są dopasowane wg [do_get_date](#do_get_date). W tej implementacji wartość jest **time_base::mdy**, odpowiadające daty w postaci 2 grudnia 1979.

### <a name="example"></a>Przykład

Zobacz przykład [date_order](#date_order), które wywołuje `do_date_order`.

## <a name="do_get"></a>  time_get::do_get

Odczytuje i konwertuje dane znakowe na wartość czasu. Akceptuje konwersji jeden specyfikator i modyfikator.

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

`first` Dane wejściowe iteratora wskazującą uruchomienia sekwencji do konwersji.

`last` Iteratora danych wejściowych, który wskazuje koniec sekwencji.

`iosbase` Obiekt stream.

`state` Pole w iosbase gdzie maski odpowiednie elementy są ustawione na wskazują błędy.

`ptm` Wskaźnik do struktury czasu, gdzie ma być przechowywany podczas.

`fmt` Znak specyfikatora konwersji.

`mod` Znak modyfikator opcjonalne.

### <a name="return-value"></a>Wartość zwracana

Zwraca określający pierwszy element nieprzekonwertowane iteratora. Ustawia błąd konwersji `ios_base::failbit` w `state` i zwraca `first`.

### <a name="remarks"></a>Uwagi

Konwertuje wirtualnej funkcji członkowskiej, z pominięciem jednej lub więcej wejściowych elementy w zakresie [`first`, `last`) do określenia wartości przechowywane w co najmniej jednego członka z `*pt`. Ustawia błąd konwersji `ios_base::failbit` w `state` i zwraca `first`. W przeciwnym razie funkcja wyznaczenie pierwszy element nieprzekonwertowane iteratora.

Specyfikatory konwersji są:

`'a'` lub `'A'` — działa tak samo jak [time_get::get_weekday](#get_weekday).

`'b'`, `'B'`, lub `'h'` — działa tak samo jak [time_get::get_monthname](#get_monthname).

`'c'` --działa tak samo jak `"%b %d %H : %M : %S %Y"`.

`'C'` --Konwertuje wartość dziesiętną pola wejściowego w zakresie [0, 99] `val` i przechowuje `val * 100 - 1900` w `pt-&tm_year`.

`'d'` lub `'e'` — Konwertuje dziesiętną pola wejściowego z zakresu [1, 31] i przechowuje wartości `pt-&tm_mday`.

`'D'` --działa tak samo jak `"%m / %d / %y"`.

`'H'` --Konwertuje dziesiętną pola wejściowego w zakresie [0, 23] i przechowuje wartości `pt-&tm_hour`.

`'I'` --Konwertuje dziesiętną pola wejściowego w zakresie [0, 11] i przechowuje wartości `pt-&tm_hour`.

`'j'` --Konwertuje dziesiętną pola wejściowego z zakresu [1, 366] i przechowuje wartości `pt-&tm_yday`.

`'m'` --Konwertuje wartość dziesiętną pola wejściowego z zakresu [1, 12] `val` i przechowuje `val - 1` w i przechowuje wartości `pt-&tm_mon`.

`'M'` --Konwertuje dziesiętną pola wejściowego w zakresie [0, 59] i przechowuje wartości `pt-&tm_min`.

`'n'` lub `'t'` — działa tak samo jak `" "`.

`'p'` --Konwertuje "M" lub "m" zero "PM" i "PM" 12 i dodaje tę wartość na `pt-&tm_hour`.

`'r'` --działa tak samo jak `"%I : %M : %S %p"`.

`'R'` --działa tak samo jak `"%H %M"`.

`'S'` --Konwertuje dziesiętną pola wejściowego w zakresie [0, 59] i przechowuje wartości `pt-&tm_sec`.

`'T'` lub `'X'` — działa tak samo jak `"%H : %M : S"`.

`'U'` --Konwertuje dziesiętną pola wejściowego w zakresie [0, 53] i przechowuje wartości `pt-&tm_yday`.

`'w'` --Konwertuje dziesiętną pola wejściowego w zakresie [0, 6] i przechowuje wartości `pt-&tm_wday`.

`'W'` --Konwertuje dziesiętną pola wejściowego w zakresie [0, 53] i przechowuje wartości `pt-&tm_yday`.

`'x'` --działa tak samo jak `"%d / %m / %y"`.

`'y'` --Konwertuje wartość dziesiętną pola wejściowego w zakresie [0, 99] `val` i przechowuje `val < 69  val + 100 : val` w `pt-&tm_year`.

`'Y'` --działa tak samo jak [time_get::get_year](#get_year).

Inne zestawy specyfikatora konwersji `ios_base::failbit` w `state` i zwraca. W tej implementacji wszelkich modyfikator nie ma znaczenia.

## <a name="do_get_date"></a>  time_get::do_get_date

A chronione wirtualnej funkcji członkowskiej wywoływaną, można przeanalizować ciągu jako data utworzonego przez *x* specyfikatora `strftime`.

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Wprowadź iteratora adresowania na początku sekwencji do skonwertowania.

`last` Wprowadź iteratora adresowania koniec sekwencji do skonwertowania.

`iosbase` Flaga formatu, który po zestaw oznacza, że symbol waluty jest opcjonalna. w przeciwnym razie jest wymagana.

`state` Ustawia elementy maski odpowiedni stan strumienia w zależności od tego, czy operacja powiodła się.

`ptm` Wskaźnik, na którym ma być przechowywane informacje o dacie.

### <a name="return-value"></a>Wartość zwracana

Wejściowy iteratora adresowania pierwszy element poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnej chroniony element członkowski próbuje dopasować sekwencyjnych elementy, rozpoczynając od pierwszego w sekwencji [ `first`, `last`) dopóki nie został rozpoznany kompletna, niepustą datę wejściowy pola. Jeśli się powiedzie, konwertuje to pole na równoważną wartość jako składniki **tm::tm\_mon**, **tm::tm\_dzień**, i **tm::tm\_roku** i przechowuje wyniki w `ptm->tm_mon`, `ptm->tm_day`, i `ptm->tm_year`odpowiednio. Zwraca iteratora wyznaczenie pierwszy element poza pole wprowadzania daty. W przeciwnym razie funkcja ustawia `iosbase::failbit` w `state`. Zwraca iteratora wyznaczenie pierwszy element poza żadnych prefiksów pola wejściowego prawidłową datą. W obu przypadkach jest równa wartości zwracanej `last`, zestawy funkcji `ios_base::eofbit` w `state`.

Format pole wprowadzania daty jest zależne. Dla domyślnych ustawień regionalnych, pole wprowadzania daty ma postać MMM DD RRRR, gdzie:

- MMM dopasowaniu wywołując [get_monthname](#get_monthname), co miesiąc.

- DD jest sekwencją cyfr dziesiętnych, którego wartość liczbową odpowiedniego musi być z zakresu [1, 31] nadanie dzień miesiąca.

- RRRR dopasowaniu wywołując [get_year](#get_year), podając roku.

Literał spacje i przecinkami musi odpowiadać odpowiednie elementy w sekwencji wejściowych.

### <a name="example"></a>Przykład

Zobacz przykład [get_date](#get_date), które wywołuje `do_get_date`.

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

`first` Wprowadź iteratora adresowania na początku sekwencji do skonwertowania.

`last` Wprowadź iteratora adresowania koniec sekwencji do skonwertowania.

`iosbase` Nieużywane.

`state` Parametr wyjściowy, który ustawia elementy maski odpowiedni stan strumienia w zależności od tego, czy operacja powiodła się.

`ptm` Wskaźnik do której ma być przechowywany informacji miesiąca.

### <a name="return-value"></a>Wartość zwracana

Wejściowy iteratora adresowania pierwszy element poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnej chroniony element członkowski próbuje dopasować sekwencyjnych elementy, rozpoczynając od pierwszego w sekwencji [ `first`, `last`) dopóki nie został rozpoznany kompletna, niepustym miesiąca wejściowy pola. Jeśli się powiedzie, konwertuje to pole na równoważną wartość jako składnik **tm::tm\_mon**i przechowuje wyniki w `ptm->tm_mon`. Zwraca iteratora wyznaczenie pierwszy element poza pole wejściowe miesiąca. W przeciwnym razie funkcja ustawia `ios_base::failbit` w *stanu*. Zwraca iteratora wyznaczenie pierwszy element poza dowolnego prefiksu prawidłowy miesiąc pola wejściowego. W obu przypadkach jest równa wartości zwracanej `last`, zestawy funkcji `ios_base::eofbit` w *stanu*.

Pole wprowadzania miesiąca jest sekwencją odpowiadający najdłuższym zestawu sekwencji specyficzne dla ustawień regionalnych, takie jak Jan, stycznia, luty lutego i tak dalej. Wartość przekonwertowana jest liczba miesięcy od stycznia.

### <a name="example"></a>Przykład

Zobacz przykład [get_monthname](#get_monthname), które wywołuje `do_get_monthname`.

## <a name="do_get_time"></a>  time_get::do_get_time

A chronione wirtualnej funkcji członkowskiej wywoływaną, można przeanalizować ciągu jako data utworzonego przez *X* specyfikatora `strftime`.

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Wprowadź iteratora adresowania na początku sekwencji do skonwertowania.

`last` Wprowadź iteratora adresowania koniec sekwencji do skonwertowania.

`iosbase` Nieużywane.

`state` Ustawia elementy maski odpowiedni stan strumienia w zależności od tego, czy operacja powiodła się.

`ptm` Wskaźnik, na którym ma być przechowywane informacje o dacie.

### <a name="return-value"></a>Wartość zwracana

Wejściowy iteratora adresowania pierwszy element poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnej chroniony element członkowski próbuje dopasować sekwencyjnych elementy, rozpoczynając od pierwszego w sekwencji [ `first`, `last`) dopóki nie został rozpoznany kompletna, czas niepustym wejściowy pola. Jeśli się powiedzie, konwertuje to pole na równoważną wartość jako składniki **tm::tm_hour**, **tm::tm_min**, i **tm::tm_sec**i przechowuje wyniki w `ptm->tm_hour`, `ptm->tm_min`, i `ptm->tm_sec`odpowiednio. Zwraca iteratora wyznaczenie pierwszy element poza pole wprowadzania godziny. W przeciwnym razie funkcja ustawia `ios_base::failbit` w *stanu*. Zwraca iteratora wyznaczenie pierwszy element poza żadnych prefiksów pola wejściowego czas ważności. W obu przypadkach jest równa wartości zwracanej `last`, zestawy funkcji `ios_base::eofbit` w *stanu*.

W tej implementacji czasu pole wejściowe ma postać ss, gdzie:

- HH jest sekwencją cyfr dziesiętnych, którego wartość liczbową odpowiedniego musi należeć do zakresu [0, 24), zapewniając godzinę dnia.

- MM jest sekwencją cyfr dziesiętnych, którego wartość liczbową odpowiedniego musi należeć do zakresu [0, 60), zapewniając minut po pełnej godzinie.

- SS jest sekwencją cyfr dziesiętnych, którego wartość liczbową odpowiedniego musi należeć do zakresu [0, 60) sekund po pełnej minucie, podając.

Dwukropki literału musi być zgodna odpowiednie elementy w sekwencji wejściowych.

### <a name="example"></a>Przykład

Zobacz przykład [get_time](#get_time), które wywołuje `do_get_time`.

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

`first` Wprowadź iteratora adresowania na początku sekwencji do skonwertowania.

`last` Wprowadź iteratora adresowania koniec sekwencji do skonwertowania.

`iosbase` Flaga formatu, który po zestaw oznacza, że symbol waluty jest opcjonalna. w przeciwnym razie jest wymagana.

`state` Ustawia elementy maski odpowiedni stan strumienia w zależności od tego, czy operacja powiodła się.

`ptm` Wskaźnik do której ma być przechowywany informacji dzień tygodnia.

### <a name="return-value"></a>Wartość zwracana

Wejściowy iteratora adresowania pierwszy element poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnej chroniony element członkowski próbuje dopasować elementy sekwencyjnych, zaczynając od `first` w sekwencji [ `first`, `last`) dopóki nie został rozpoznany kompletna, niepustym dzień tygodnia wejściowy pola. Jeśli się powiedzie, konwertuje to pole na równoważną wartość jako składnik **tm::tm\_członka**i przechowuje wyniki w `ptm->tm_wday`. Zwraca iteratora wyznaczenie pierwszy element poza pole wejściowe dzień tygodnia. W przeciwnym razie funkcja ustawia `ios_base::failbit` w *stanu*. Zwraca iteratora wyznaczenie pierwszy element poza żadnych prefiksów pola wejściowego nieprawidłowy dzień tygodnia. W obu przypadkach jest równa wartości zwracanej `last`, zestawy funkcji `ios_base::eofbit` w *stanu*.

Pole wprowadzania dzień tygodnia jest sekwencją odpowiadający najdłuższym zestawu sekwencji specyficzne dla ustawień regionalnych, takie jak Sun, niedziela, Mon poniedziałek i tak dalej. Skonwertowana wartość jest liczbą dni od niedzieli.

### <a name="example"></a>Przykład

Zobacz przykład [get_weekday](#get_weekday), które wywołuje `do_get_weekday`.

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

`first` Wprowadź iteratora adresowania na początku sekwencji do skonwertowania.

`last` Wprowadź iteratora adresowania koniec sekwencji do skonwertowania.

`iosbase` Flaga formatu, który po zestaw oznacza, że symbol waluty jest opcjonalna. w przeciwnym razie jest wymagana.

`state` Ustawia elementy maski odpowiedni stan strumienia w zależności od tego, czy operacja powiodła się.

`ptm` Wskaźnik do której ma być przechowywany informacji roku.

### <a name="return-value"></a>Wartość zwracana

Wejściowy iteratora adresowania pierwszy element poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnej chroniony element członkowski próbuje dopasować elementy sekwencyjnych, zaczynając od `first` w sekwencji [ `first`, `last`) dopóki nie został rozpoznany kompletna, niepustym roku wejściowy pola. Jeśli się powiedzie, konwertuje to pole na równoważną wartość jako składnik **tm::tm\_roku**i przechowuje wyniki w `ptm->tm_year`. Zwraca iteratora wyznaczenie pierwszy element poza pole wejściowe roku. W przeciwnym razie funkcja ustawia `ios_base::failbit` w *stanu*. Zwraca iteratora wyznaczenie pierwszy element poza dowolnego prefiksu prawidłowy rok pola wejściowego. W obu przypadkach jest równa wartości zwracanej `last`, zestawy funkcji `ios_base::eofbit` w *stanu*.

Pole wprowadzania roku jest sekwencją cyfr dziesiętnych, którego wartość liczbową odpowiedniego musi należeć do zakresu [1900, 2036). Wartość przechowywana jest ta wartość minus 1900. W tej implementacji wartości z zakresu [69, 136) reprezentują zakresu lat [1969, 2036). Wartości w zakresie [0, 69) również są dopuszczalne, ale może reprezentować zakresu lat [1900, 1969) lub [2000, 2069), w zależności od środowiska określone.

### <a name="example"></a>Przykład

Zobacz przykład [get_year](#get_year), które wywołuje `do_get_year`.

## <a name="get"></a>  time_get::Get

Odczytuje ze źródła danych znakowych i konwertuje te dane na czas, który jest przechowywany w strukturze czasu. Akceptuje pierwszej funkcji konwersji jeden specyfikator i modyfikator, drugi akceptuje kilku.

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

`first` Wprowadź iteratora wskazującą, w którym rozpoczyna się wykonanie sekwencji do skonwertowania.

`last` Wejściowy iteratora wskazuje koniec sekwencji do skonwertowania.

`iosbase` Strumień.

`state` Elementy odpowiednie maski są ustawione dla stan strumienia wskazać błędy.

`ptm` Wskaźnik do struktury czasu, w którym ma być przechowywany podczas.

`fmt` Znak specyfikatora konwersji.

`mod` Znak modyfikator opcjonalne.

`fmt_first` Wskazuje gdzie uruchomić dyrektywy formatu.

`fmt_last` Wskazuje koniec dyrektywy formatu.

### <a name="return-value"></a>Wartość zwracana

Zwraca iteratora dane, które zostało użyte do przypisywania struktury czas do pierwszego znaku `*ptm`.

### <a name="remarks"></a>Uwagi

Zwraca pierwszy funkcji członkowskiej `do_get(first, last, iosbase, state, ptm, fmt, mod)`.

Drugi wywołania funkcji Członkowskich `do_get` pod kontrolą format rozdzielone `[fmt_first, fmt_last)`. Format traktuje jako sekwencję pól, z których każdy określa konwersji zero lub więcej wejściowych elementy rozdzielone `[first, last)`. Zwraca wyznaczenie pierwszy element nieprzekonwertowane iteratora. Istnieją trzy typy pól:

Procent (%), w formacie, a następnie modyfikatora opcjonalne `mod` w zestawie EOQ #, a następnie specyfikatora konwersji `fmt`, zastępuje `first` z wartością zwróconą przez `do_get(first, last, iosbase, state, ptm, fmt, mod)`. Ustawia błąd konwersji `ios_base::failbit` w `state` i zwraca.

Element odstępu, w formacie pomija zero lub więcej wejściowych elementy odstępu.

Element format musi być zgodna następny element wejściowy jest pomijana. Niepowodzenie dopasowania ustawia `ios_base::failbit` w `state` i zwraca.

## <a name="get_date"></a>  time_get::get_date

Analizuje ciąg jako data utworzonego przez *x* specyfikatora `strftime`.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Wprowadź iteratora adresowania na początku sekwencji do skonwertowania.

`last` Wprowadź iteratora adresowania koniec sekwencji do skonwertowania.

`iosbase` Flaga formatu, który po zestaw oznacza, że symbol waluty jest opcjonalna. w przeciwnym razie jest wymagana.

`state` Ustawia elementy maski odpowiedni stan strumienia w zależności od tego, czy operacja powiodła się.

`ptm` Wskaźnik, na którym ma być przechowywane informacje o dacie.

### <a name="return-value"></a>Wartość zwracana

Wejściowy iteratora adresowania pierwszy element poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_get_date](#do_get_date)( `first`, `last`, `iosbase`, `state`, `ptm`).

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

`first` Wprowadź iteratora adresowania na początku sekwencji do skonwertowania.

`last` Wprowadź iteratora adresowania koniec sekwencji do skonwertowania.

`iosbase` Nieużywane.

`state` Parametr wyjściowy, który ustawia elementy maski odpowiedni stan strumienia w zależności od tego, czy operacja powiodła się.

`ptm` Wskaźnik do której ma być przechowywany informacji miesiąca.

### <a name="return-value"></a>Wartość zwracana

Wejściowy iteratora adresowania pierwszy element poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_get_monthname](#do_get_monthname)( `first`, `last`, `iosbase`, `state`, `ptm`).

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

Analizuje ciąg jako data utworzonego przez *X* specyfikatora `strftime`.

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Wprowadź iteratora adresowania na początku sekwencji do skonwertowania.

`last` Wprowadź iteratora adresowania koniec sekwencji do skonwertowania.

`iosbase` Nieużywane.

`state` Ustawia elementy maski odpowiedni stan strumienia w zależności od tego, czy operacja powiodła się.

`ptm` Wskaźnik, na którym ma być przechowywane informacje o dacie.

### <a name="return-value"></a>Wartość zwracana

Wejściowy iteratora adresowania pierwszy element poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_get_time](#do_get_time)( `first`, `last`, `iosbase`, `state`, `ptm`).

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

`first` Wprowadź iteratora adresowania na początku sekwencji do skonwertowania.

`last` Wprowadź iteratora adresowania koniec sekwencji do skonwertowania.

`iosbase` Flaga formatu, który po zestaw oznacza, że symbol waluty jest opcjonalna. w przeciwnym razie jest wymagana.

`state` Ustawia elementy maski odpowiedni stan strumienia w zależności od tego, czy operacja powiodła się.

`ptm` Wskaźnik do której ma być przechowywany informacji dzień tygodnia.

### <a name="return-value"></a>Wartość zwracana

Wejściowy iteratora adresowania pierwszy element poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_get_weekday](#do_get_weekday)( `first`, `last`, `iosbase`, `state`, `ptm`).

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

`first` Wprowadź iteratora adresowania na początku sekwencji do skonwertowania.

`last` Wprowadź iteratora adresowania koniec sekwencji do skonwertowania.

`iosbase` Flaga formatu, który po zestaw oznacza, że symbol waluty jest opcjonalna. w przeciwnym razie jest wymagana.

`state` Ustawia elementy maski odpowiedni stan strumienia w zależności od tego, czy operacja powiodła się.

`ptm` Wskaźnik do której ma być przechowywany informacji roku.

### <a name="return-value"></a>Wartość zwracana

Wejściowy iteratora adresowania pierwszy element poza pole wejściowe.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_get_year](#do_get_year)( `first`, `last`, `iosbase`, `state`, `ptm`).

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

Typ jest synonimem parametru szablonu **InputIterator**.

## <a name="time_get"></a>  time_get::time_get

Konstruktor dla obiektów typu `time_get`.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

`refs` Wartość całkowita używany do określania typu zarządzania pamięci dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości `refs` i ich znaczenie są:

- 0: okres istnienia obiektu zarządza ustawieniami regionalnymi, które zawierałoby proces.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: te wartości są niezdefiniowane.

Nie bezpośredniego przykładów to możliwe, ponieważ destruktor jest chroniony.

Konstruktor inicjuje jego obiektu podstawowego z **locale::**[aspektu](../standard-library/locale-class.md#facet_class)( `refs`).

## <a name="see-also"></a>Zobacz także

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[time_base, klasa](../standard-library/time-base-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

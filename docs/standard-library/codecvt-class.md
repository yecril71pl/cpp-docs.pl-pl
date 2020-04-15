---
title: codecvt — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt
- xlocale/std::codecvt::extern_type
- xlocale/std::codecvt::intern_type
- xlocale/std::codecvt::state_type
- xlocale/std::codecvt::always_noconv
- xlocale/std::codecvt::do_always_noconv
- xlocale/std::codecvt::do_encoding
- xlocale/std::codecvt::do_in
- xlocale/std::codecvt::do_length
- xlocale/std::codecvt::do_max_length
- xlocale/std::codecvt::do_out
- xlocale/std::codecvt::do_unshift
- xlocale/std::codecvt::encoding
- xlocale/std::codecvt::in
- xlocale/std::codecvt::length
- xlocale/std::codecvt::max_length
- xlocale/std::codecvt::out
- xlocale/std::codecvt::unshift
helpviewer_keywords:
- std::codecvt [C++]
- std::codecvt [C++], extern_type
- std::codecvt [C++], intern_type
- std::codecvt [C++], state_type
- std::codecvt [C++], always_noconv
- std::codecvt [C++], do_always_noconv
- std::codecvt [C++], do_encoding
- std::codecvt [C++], do_in
- std::codecvt [C++], do_length
- std::codecvt [C++], do_max_length
- std::codecvt [C++], do_out
- std::codecvt [C++], do_unshift
- std::codecvt [C++], encoding
- std::codecvt [C++], in
- std::codecvt [C++], length
- std::codecvt [C++], max_length
- std::codecvt [C++], out
- std::codecvt [C++], unshift
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
ms.openlocfilehash: 3dba971b112c23325e0529e53746cbee827df5e9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371950"
---
# <a name="codecvt-class"></a>codecvt — Klasa

Szablon klasy opisujący obiekt, który może służyć jako aspekt ustawień regionalnych. Jest w stanie kontrolować konwersje między sekwencją wartości używaną do kodowania znaków w ramach programu i sekwencją wartości używanych do kodowania znaków poza programem.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ używany w programie do kodowania znaków.

*Bajtów*\
Typ używany do kodowania znaków poza programem.

*Typ stanu*\
Typ, który może służyć do reprezentowania pośrednich stanów konwersji między typami wewnętrznymi i zewnętrznymi reprezentacji znaków.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który może służyć jako [aspekt ustawień regionalnych,](../standard-library/locale-class.md#facet_class)aby kontrolować konwersje między sekwencją wartości typu *CharType* a sekwencją wartości typu *Bajt*. Klasa *StateType* charakteryzuje transformację — a obiekt klasy *StateType* przechowuje wszystkie niezbędne informacje o stanie podczas konwersji.

Wewnętrzne kodowanie używa reprezentacji ze stałą liczbą bajtów na znak, zwykle typu **char** lub type **wchar_t**.

Podobnie jak w przypadku dowolnego aspektu ustawień regionalnych, obiekt `id` statyczny ma początkową wartość przechowywaną w wysokości zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości `id`przechowuje unikatową wartość dodatnią w programie .

Wersje szablonów [do_in](#do_in) i [do_out](#do_out) zawsze zwracają `codecvt_base::noconv`.

Standardowa biblioteka języka C++ definiuje kilka jawnych specjalizacji:

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

konwertuje między **sekwencjami wchar_t** i **char.**

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

konwertuje `char16_t` sekwencje zakodowane jako sekwencje UTF-16 i **char** zakodowane jako UTF-8.

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

konwertuje `char32_t` sekwencje zakodowane jako SEKWENCJE UTF-32 (UCS-4) i **char** zakodowane jako UTF-8.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[kodekvt](#codecvt)|Konstruktor dla obiektów `codecvt` klasy, który służy jako aspekt ustawień regionalnych do obsługi konwersji.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[extern_type](#extern_type)|Typ znaku, który jest używany dla zewnętrznych reprezentacji.|
|[intern_type](#intern_type)|Typ znaku, który jest używany dla wewnętrznych reprezentacji.|
|[state_type](#state_type)|Typ znaku, który jest używany do reprezentowania pośrednich stanów w czasie konwersji między wewnętrznymi i zewnętrznymi reprezentacjami.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[always_noconv](#always_noconv)|Sprawdza, czy nie trzeba wykonać żadnych konwersji.|
|[do_always_noconv](#do_always_noconv)|Funkcja wirtualna wywoływana w celu sprawdzenia, czy nie trzeba wykonywać żadnych konwersji.|
|[do_encoding](#do_encoding)|Funkcja wirtualna, która sprawdza, `Byte` czy kodowanie strumienia jest `Byte` zależne od `CharType` stanu, czy stosunek między wartościami używanymi a wartościami wyprodukowanymi jest stała, a jeśli tak, określa wartość tego współczynnika.|
|[do_in](#do_in)|Funkcja wirtualna wywoływana do `Byte` konwertowania sekwencji wartości wewnętrznych na sekwencję wartości zewnętrznych. `CharType`|
|[do_length](#do_length)|Funkcja wirtualna, która `Byte` określa, ile wartości `Byte` z danej sekwencji wartości zewnętrznych `CharType` wytwarza nie więcej `Byte` niż podana liczba wartości wewnętrznych i zwraca tę liczbę wartości.|
|[do_max_length](#do_max_length)|Funkcja wirtualna, która zwraca maksymalną liczbę bajtów zewnętrznych niezbędnych do wyprodukowania jednego wewnętrznego `CharType`.|
|[do_out](#do_out)|Funkcja wirtualna wywoływana do `CharType` konwertowania sekwencji wartości wewnętrznych na sekwencję bajtów zewnętrznych.|
|[do_unshift](#do_unshift)|Funkcja wirtualna wywoływana `Byte` w celu zapewnienia wartości wymaganych w konwersji `Byte` zależnej od stanu, aby zakończyć ostatni znak w sekwencji wartości.|
|[Kodowania](#encoding)|Testy, jeśli kodowanie `Byte` strumienia jest zależne od `Byte` stanu, `CharType` czy stosunek między wartościami używanymi i wartości produkowanych jest stała, a jeśli tak, określa wartość tego współczynnika.|
|[in](#in)|Konwertuje zewnętrzną reprezentację `Byte` sekwencji wartości na wewnętrzną reprezentację sekwencji `CharType` wartości.|
|[Długość](#length)|Określa, ile `Byte` wartości z danej `Byte` sekwencji wartości zewnętrznych wytwarza nie `CharType` więcej niż daną liczbę wartości wewnętrznych i zwraca tę liczbę `Byte` wartości.|
|[max_length](#max_length)|Zwraca maksymalną liczbę `Byte` wartości zewnętrznych niezbędnych `CharType`do wyprodukowania jednego wewnętrznego .|
|[na zewnątrz](#out)|Konwertuje sekwencję `CharType` wartości wewnętrznych na `Byte` sekwencję wartości zewnętrznych.|
|[odłączyć](#unshift)|Zawiera wartości `Byte` zewnętrzne potrzebne w konwersji zależnej od stanu, `Byte` aby zakończyć ostatni znak w sekwencji wartości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="codecvtalways_noconv"></a><a name="always_noconv"></a>kodekvt::always_noconv

Sprawdza, czy nie trzeba przeprowadzać konwersji.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna, która jest **prawdziwa,** jeśli nie trzeba przeprowadzać konwersji; **false,** jeśli co najmniej jeden musi być zrobione.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_always_noconv](#do_always_noconv).

### <a name="example"></a>Przykład

```cpp
// codecvt_always_noconv.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = use_facet<codecvt<char, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result1 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;

   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result2 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;
}
```

```Output
No conversion is needed.
At least one conversion is required.
```

## <a name="codecvtcodecvt"></a><a name="codecvt"></a>kodekvt::kodekvt

Konstruktor dla obiektów klasy codecvt, który służy jako aspekt ustawień regionalnych do obsługi konwersji.

```cpp
explicit codecvt(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

*Bibl*\
Wartość całkowita używana do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *refs* i ich znaczenie to:

- 0: Okres istnienia obiektu jest zarządzany przez ustawienia regionalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- 2: Te wartości nie są zdefiniowane.

Konstruktor inicjuje swój `locale::facet` obiekt bazowy za pomocą ustawień [regionalnych::facet](../standard-library/locale-class.md#facet_class)`(refs)`.

## <a name="codecvtdo_always_noconv"></a><a name="do_always_noconv"></a>kodekvt::do_always_noconv

Funkcja wirtualna wywoływana do testowania, czy nie trzeba wykonywać konwersji.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja chronionego wirtualnego elementu członkowskiego zwraca **wartość true** tylko wtedy, `noconv`gdy każde wywołanie [do_in](#do_in) lub [do_out](#do_out) zwraca .

Wersja szablonu zawsze zwraca **true**.

### <a name="example"></a>Przykład

Zobacz przykład [always_noconv](#always_noconv), który wywołuje `do_always_noconv`.

## <a name="codecvtdo_encoding"></a><a name="do_encoding"></a>kodekvt::do_kodowanie

Funkcja wirtualna, która sprawdza, `Byte` czy kodowanie strumienia jest `Byte` zależne od `CharType` stanu, czy stosunek między wartościami używanymi a wartościami wyprodukowanymi jest stała, a jeśli tak, określa wartość tego współczynnika.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja chronionego elementu członkowskiego wirtualnego zwraca:

- -1, jeśli kodowanie sekwencji `extern_type` typu jest zależne od stanu.

- 0, jeśli kodowanie obejmuje sekwencje o różnej długości.

- *N*, jeśli kodowanie obejmuje tylko sekwencje o długości *N*

### <a name="example"></a>Przykład

Zobacz przykład [kodowania](#encoding), `do_encoding`który wywołuje .

## <a name="codecvtdo_in"></a><a name="do_in"></a>kodekvt::do_in

Funkcja wirtualna wywoływana do `Byte` konwertowania sekwencji wartości zewnętrznych na sekwencję wartości wewnętrznych. `CharType`

```cpp
virtual result do_in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parametry

*Państwa*\
Stan konwersji, który jest utrzymywany między wywołaniami funkcji elementu członkowskiego.

*po pierwsze1*\
Wskaźnik do początku sekwencji, która ma zostać przekonwertowana.

*ostatni1*\
Wskaźnik do końca sekwencji, która ma zostać przekonwertowana.

*następny1*\
Wskaźnik poza koniec przekonwertowane sekwencji do pierwszego nieprzekształconego znaku.

*pierwszy2*\
Wskaźnik do początku przekonwertowanej sekwencji.

*ostatni2*\
Wskaźnik do końca przekonwertowanej sekwencji.

*następny2*\
Wskaźnik do `CharType` tego, który pojawia `CharType`się po ostatniej konwersji , do pierwszego niezmiennego znaku w sekwencji docelowej.

### <a name="return-value"></a>Wartość zwracana

Zwrot, który wskazuje na powodzenie, częściowy sukces lub niepowodzenie operacji. Funkcja zwraca:

- `codecvt_base::error`jeśli sekwencja źródłowsza jest źle utworzona.

- `codecvt_base::noconv`jeśli funkcja nie wykonuje konwersji.

- `codecvt_base::ok`jeśli konwersja zakończy się pomyślnie.

- `codecvt_base::partial`jeśli źródło jest niewystarczające lub jeśli miejsce docelowe nie jest wystarczająco duże, aby konwersja powiodła się.

### <a name="remarks"></a>Uwagi

*stan* konwersji początkowej na początku nowej sekwencji źródłowej. Funkcja zmienia swoją przechowywaną wartość w razie potrzeby, aby odzwierciedlić bieżący stan pomyślnej konwersji. Jego wartość przechowywana jest w inny sposób nieokreślona.

### <a name="example"></a>Przykład

Zobacz przykład [w](#in), `do_in`który wywołuje .

## <a name="codecvtdo_length"></a><a name="do_length"></a>kodekvt::do_length

Funkcja wirtualna, która `Byte` określa, ile wartości `Byte` z danej sekwencji wartości zewnętrznych `CharType` wytwarza nie więcej `Byte` niż podana liczba wartości wewnętrznych i zwraca tę liczbę wartości.

```cpp
virtual int do_length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Parametry

*Państwa*\
Stan konwersji, który jest utrzymywany między wywołaniami funkcji elementu członkowskiego.

*po pierwsze1*\
Wskaźnik do początku sekwencji zewnętrznej.

*ostatni1*\
Wskaźnik do końca sekwencji zewnętrznej.

*len2 (len2)*\
Maksymalna liczba `Byte` wartości, które mogą być zwracane przez funkcję elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita reprezentująca liczbę maksymalnej liczby konwersji, nie większej niż *len2,* zdefiniowanej `first1` `last1`przez sekwencję źródeł zewnętrznych w [ , ).

### <a name="remarks"></a>Uwagi

Funkcja chronionego wirtualnego `do_in( state, first1, last1, next1, buf, buf + len2, next2)` elementu członkowskiego skutecznie wywołuje *stan* `buf`(kopię stanu), niektóre bufory `next1` i wskaźniki oraz `next2`.

Następnie zwraca `next2`  -  `buf`. W związku z tym zlicza maksymalną liczbę konwersji, nie większą `first1`niż `last1` *len2,* zdefiniowaną przez sekwencję źródłową w [ , ).

Wersja szablonu zawsze zwraca mniejszą z *last1* - *first1* i *len2*.

### <a name="example"></a>Przykład

Zobacz przykład [długości](#length), `do_length`który wywołuje .

## <a name="codecvtdo_max_length"></a><a name="do_max_length"></a>kodekvt::do_max_length

Funkcja wirtualna, która zwraca `Byte` maksymalną liczbę wartości `CharType`zewnętrznych niezbędnych do wyprodukowania jednego wewnętrznego .

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba `Byte` wartości niezbędnych `CharType`do wyprodukowania jednego .

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego wirtualnego zwraca największą dopuszczalną wartość, która może zostać zwrócona przez [do_length](#do_length) `( first1, last1, 1)` dla dowolnych prawidłowych wartości *first1* i *last1*.

### <a name="example"></a>Przykład

Zobacz przykład [max_length](#max_length), który `do_max_length`wywołuje .

## <a name="codecvtdo_out"></a><a name="do_out"></a>kodekvt::do_out

Funkcja wirtualna wywoływana do `CharType` konwertowania sekwencji wartości wewnętrznych na sekwencję wartości zewnętrznych. `Byte`

```cpp
virtual result do_out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*Państwa*\
Stan konwersji, który jest utrzymywany między wywołaniami funkcji elementu członkowskiego.

*po pierwsze1*\
Wskaźnik do początku sekwencji, która ma zostać przekonwertowana.

*ostatni1*\
Wskaźnik do końca sekwencji, która ma zostać przekonwertowana.

*następny1*\
Odwołanie do wskaźnika do pierwszego `CharType`nieprzekształcony `CharType` , po ostatniej konwersji.

*pierwszy2*\
Wskaźnik do początku przekonwertowanej sekwencji.

*ostatni2*\
Wskaźnik do końca przekonwertowanej sekwencji.

*następny2*\
Odwołanie do wskaźnika do pierwszego `Byte`nieprzekształcony `Byte` , po ostatniej konwersji.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca:

- `codecvt_base::error`jeśli sekwencja źródłowsza jest źle utworzona.

- `codecvt_base::noconv`jeśli funkcja nie wykonuje konwersji.

- `codecvt_base::ok`jeśli konwersja zakończy się pomyślnie.

- `codecvt_base::partial`jeśli źródło jest niewystarczające lub jeśli miejsce docelowe nie jest wystarczająco duże, aby konwersja powiodła się.

### <a name="remarks"></a>Uwagi

*stan* konwersji początkowej na początku nowej sekwencji źródłowej. Funkcja zmienia swoją przechowywaną wartość w razie potrzeby, aby odzwierciedlić bieżący stan pomyślnej konwersji. Jego wartość przechowywana jest w inny sposób nieokreślona.

### <a name="example"></a>Przykład

Zobacz przykład [out](#out), `do_out`który wywołuje .

## <a name="codecvtdo_unshift"></a><a name="do_unshift"></a>kodekvt::do_unshift

Funkcja wirtualna wywoływana `Byte` w celu zapewnienia wartości wymaganych w konwersji `Byte` zależnej od stanu, aby zakończyć ostatni znak w sekwencji wartości.

```cpp
virtual result do_unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*Państwa*\
Stan konwersji, który jest utrzymywany między wywołaniami funkcji elementu członkowskiego.

*pierwszy2*\
Wskaźnik do pierwszej pozycji w zakresie docelowym.

*ostatni2*\
Wskaźnik do ostatniej pozycji w zakresie docelowym.

*następny2*\
Wskaźnik do pierwszego elementu bez cienia w sekwencji docelowej.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca:

- `codecvt_base::error`jeśli *stan* reprezentuje nieprawidłowy stan

- `codecvt_base::noconv`jeśli funkcja nie wykonuje konwersji

- `codecvt_base::ok`jeśli konwersja zakończy się pomyślnie

- `codecvt_base::partial`jeśli cel nie jest wystarczająco duży, aby konwersja powiodła się

### <a name="remarks"></a>Uwagi

Funkcja chronionego wirtualnego elementu członkowskiego `CharType`próbuje przekonwertować element źródłowy (0) na sekwencję docelową, która przechowuje w obrębie [ `first2`, `last2`), z wyjątkiem elementu `Byte`kończącego (0). Zawsze przechowuje w *next2* wskaźnik do pierwszego elementu bez elementów w sekwencji docelowej.

_ *Państwo* musi reprezentować początkowy stan konwersji na początku nowej sekwencji źródłowej. Funkcja zmienia swoją przechowywaną wartość w razie potrzeby, aby odzwierciedlić bieżący stan pomyślnej konwersji. Zazwyczaj konwersja elementu `CharType`źródłowego (0) pozostawia bieżący stan w początkowym stanie konwersji.

### <a name="example"></a>Przykład

Zobacz przykład [unshift](#unshift), `do_unshift`który wywołuje .

## <a name="codecvtencoding"></a><a name="encoding"></a>kodekvt::kodowanie

Testy, jeśli kodowanie `Byte` strumienia jest zależne od `Byte` stanu, `CharType` czy stosunek między wartościami używanymi i wartości produkowanych jest stała, a jeśli tak, określa wartość tego współczynnika.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli zwracana wartość jest dodatnia, ta `Byte` wartość jest stałą liczbą znaków wymaganych do wytworzenia `CharType` znaku.

Funkcja chronionego elementu członkowskiego wirtualnego zwraca:

- -1, jeśli kodowanie sekwencji `extern_type` typu jest zależne od stanu.

- 0, jeśli kodowanie obejmuje sekwencje o różnej długości.

- *N*, jeśli kodowanie obejmuje tylko sekwencje o długości *N.*

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_encoding](#do_encoding).

### <a name="example"></a>Przykład

```cpp
// codecvt_encoding.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   int result1 = use_facet<codecvt<char, char, mbstate_t> > ( loc ).encoding ( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
}
```

```Output
1
1
1
```

## <a name="codecvtextern_type"></a><a name="extern_type"></a>kodekvt::extern_type

Typ znaku, który jest używany dla zewnętrznych reprezentacji.

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `Byte`szablonu .

## <a name="codecvtin"></a><a name="in"></a>kodekvt::w

Konwertuje zewnętrzną reprezentację `Byte` sekwencji wartości na wewnętrzną reprezentację sekwencji `CharType` wartości.

```cpp
result in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parametry

*Państwa*\
Stan konwersji, który jest utrzymywany między wywołaniami funkcji elementu członkowskiego.

*po pierwsze1*\
Wskaźnik do początku sekwencji, która ma zostać przekonwertowana.

*ostatni1*\
Wskaźnik do końca sekwencji, która ma zostać przekonwertowana.

*następny1*\
Wskaźnik poza koniec przekonwertowane sekwencji do pierwszego nieprzekonwertowanego znaku.

*pierwszy2*\
Wskaźnik do początku przekonwertowanej sekwencji.

*ostatni2*\
Wskaźnik do końca przekonwertowanej sekwencji.

*następny2*\
Wskaźnik do `CharType` tego pojawia się `Chartype` po ostatniej konwersji do pierwszego niezmiennego znaku w sekwencji docelowej.

### <a name="return-value"></a>Wartość zwracana

Zwrot, który wskazuje na powodzenie, częściowy sukces lub niepowodzenie operacji. Funkcja zwraca:

- `codecvt_base::error`jeśli sekwencja źródłowsza jest źle utworzona.

- `codecvt_base::noconv`jeśli funkcja nie wykonuje konwersji.

- `codecvt_base::ok`jeśli konwersja zakończy się pomyślnie.

- `codecvt_base::partial`jeśli źródło jest niewystarczające lub jeśli miejsce docelowe nie jest wystarczająco duże, aby konwersja powiodła się.

### <a name="remarks"></a>Uwagi

*stan* konwersji początkowej na początku nowej sekwencji źródłowej. Funkcja zmienia swoją przechowywaną wartość, w razie potrzeby, aby odzwierciedlić bieżący stan pomyślnej konwersji. Po częściowej konwersji *stan* musi być ustawiony tak, aby umożliwić wznowienie konwersji po nadejściu nowych znaków.

Funkcja elementu członkowskiego zwraca [do_in](#do_in)`( state, first1,  last1,  next1, first2, last2,  next2)`.

### <a name="example"></a>Przykład

```cpp
// codecvt_in.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));
   const char* pszNext;
   wchar_t* pwszNext;
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).in( state,
          pszExt, &pszExt[strlen(pszExt)], pszNext,
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error)  L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;
   exit(-1);
}
```

```Output
It worked! The converted string is:
[This is the string to be converted!]
```

## <a name="codecvtintern_type"></a><a name="intern_type"></a>kodekvt::intern_type

Typ znaku, który jest używany dla wewnętrznych reprezentacji.

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `CharType`szablonu .

## <a name="codecvtlength"></a><a name="length"></a>kodekvt::długość

Określa, ile `Byte` wartości z danej `Byte` sekwencji wartości zewnętrznych wytwarza nie `CharType` więcej niż daną liczbę wartości wewnętrznych i zwraca tę liczbę `Byte` wartości.

```cpp
int length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Parametry

*Państwa*\
Stan konwersji, który jest utrzymywany między wywołaniami funkcji elementu członkowskiego.

*po pierwsze1*\
Wskaźnik do początku sekwencji zewnętrznej.

*ostatni1*\
Wskaźnik do końca sekwencji zewnętrznej.

*len2 (len2)*\
Maksymalna liczba bajtów, które mogą być zwracane przez funkcję elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita reprezentująca liczbę maksymalnej liczby konwersji, nie większej niż *len2,* zdefiniowanej `first1` `last1`przez sekwencję źródeł zewnętrznych w [ , ).

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_length](#do_length)`( state, first1, last1, len2)`.

### <a name="example"></a>Przykład

```cpp
// codecvt_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   char* pszExt = "This is the string whose length is to be measured!";
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).length( state,
          pszExt, &pszExt[strlen(pszExt)], LEN );
   cout << "The length of the string is: ";
   wcout << res;
   cout << "." << endl;
   exit(-1);
}
```

```Output
The length of the string is: 50.
```

## <a name="codecvtmax_length"></a><a name="max_length"></a>kodekvt::max_length

Zwraca maksymalną liczbę `Byte` wartości zewnętrznych niezbędnych `CharType`do wyprodukowania jednego wewnętrznego .

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba `Byte` wartości niezbędnych `CharType`do wyprodukowania jednego .

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_max_length](#do_max_length).

### <a name="example"></a>Przykład

```cpp
// codecvt_max_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc( "C");//English_Britain" );//German_Germany
   int res = use_facet<codecvt<char, char, mbstate_t> >
     ( loc ).max_length( );
   wcout << res << endl;
}
```

```Output
1
```

## <a name="codecvtout"></a><a name="out"></a>kodekvt::out

Konwertuje sekwencję `CharType` wartości wewnętrznych na `Byte` sekwencję wartości zewnętrznych.

```cpp
result out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*Państwa*\
Stan konwersji, który jest utrzymywany między wywołaniami funkcji elementu członkowskiego.

*po pierwsze1*\
Wskaźnik do początku sekwencji, która ma zostać przekonwertowana.

*ostatni1*\
Wskaźnik do końca sekwencji, która ma zostać przekonwertowana.

*następny1*\
Odwołanie do wskaźnika do pierwszego `CharType` nieprzekształcony po ostatniej `CharType` konwersji.

*pierwszy2*\
Wskaźnik do początku przekonwertowanej sekwencji.

*ostatni2*\
Wskaźnik do końca przekonwertowanej sekwencji.

*następny2*\
Odwołanie do wskaźnika do pierwszego `Byte` nieprzekształcony `Byte`po ostatniej przekonwertowane .

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca [do_out](#do_out)`( state, first1, last1, next1, first2, last2, next2)`.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [codecvt::do_out](#do_out).

### <a name="example"></a>Przykład

```cpp
// codecvt_out.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
#include <wchar.h>
using namespace std;
#define LEN 90
int main( )
{
   char pszExt[LEN+1];
   wchar_t *pwszInt = L"This is the wchar_t string to be converted.";
   memset( &pszExt[0], 0, ( sizeof( char ) )*( LEN+1 ) );
   char* pszNext;
   const wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).out( state,
      pwszInt, &pwszInt[wcslen( pwszInt )], pwszNext ,
      pszExt, &pszExt[wcslen( pwszInt )], pszNext );
   pszExt[wcslen( pwszInt )] = 0;
   cout << ( ( res!=codecvt_base::error )  "It worked: " : "It didn't work: " )
   << "The converted string is:\n ["
   << &pszExt[0]
   << "]" << endl;
}
```

```Output
It worked: The converted string is:
[This is the wchar_t string to be converted.]
```

## <a name="codecvtstate_type"></a><a name="state_type"></a>kodekvt::state_type

Typ znaku, który jest używany do reprezentowania pośrednich stanów w czasie konwersji między wewnętrznymi i zewnętrznymi reprezentacjami.

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `StateType`szablonu .

## <a name="codecvtunshift"></a><a name="unshift"></a>kodekvt::unshift

Zawiera `Byte` wartości potrzebne w konwersji zależnej od stanu, `Byte` aby zakończyć ostatni znak w sekwencji wartości.

```cpp
result unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*Państwa*\
Stan konwersji, który jest utrzymywany między wywołaniami funkcji elementu członkowskiego.

*pierwszy2*\
Wskaźnik do pierwszej pozycji w zakresie docelowym.

*ostatni2*\
Wskaźnik do ostatniej pozycji w zakresie docelowym.

*następny2*\
Wskaźnik do pierwszego elementu bez cienia w sekwencji docelowej.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca:

- `codecvt_base::error`jeśli stan reprezentuje nieprawidłowy stan.

- `codecvt_base::noconv`jeśli funkcja nie wykonuje konwersji.

- `codecvt_base::ok`jeśli konwersja zakończy się pomyślnie.

- `codecvt_base::partial`jeśli miejsce docelowe nie jest wystarczająco duże, aby konwersja powiodła się.

### <a name="remarks"></a>Uwagi

Funkcja chronionego wirtualnego elementu członkowskiego `CharType`próbuje przekonwertować element źródłowy (0) na sekwencję docelową, która przechowuje w obrębie [ `first2`, `last2`), z wyjątkiem elementu `Byte`kończącego (0). Zawsze przechowuje w *next2* wskaźnik do pierwszego elementu bez elementów w sekwencji docelowej.

*stan* konwersji początkowej na początku nowej sekwencji źródłowej. Funkcja zmienia swoją przechowywaną wartość, w razie potrzeby, aby odzwierciedlić bieżący stan pomyślnej konwersji. Zazwyczaj konwersja elementu `CharType`źródłowego (0) pozostawia bieżący stan w początkowym stanie konwersji.

Funkcja elementu członkowskiego zwraca [do_unshift](#do_unshift)`( state, first2, last2, next2 )`.

## <a name="see-also"></a>Zobacz też

[\<>ustawień regionalnych](../standard-library/locale.md)\
[Strony kodowe](../c-runtime-library/code-pages.md)\
[Nazwy ustawień regionalnych, języki i ciągi kraju/regionu](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

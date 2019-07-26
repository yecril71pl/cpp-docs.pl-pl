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
ms.openlocfilehash: 936b3ab63b454e8f7e0490c2d155356a7c3b240f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459831"
---
# <a name="codecvt-class"></a>codecvt — Klasa

Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych. Jest w stanie kontrolować konwersje między sekwencją wartości używaną do kodowania znaków w ramach programu i sekwencją wartości używanych do kodowania znaków poza programem.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ używany w programie do kodowania znaków.

*Bajc*\
Typ używany do kodowania znaków poza programem.

*StateType*\
Typ, który może służyć do reprezentowania pośrednich stanów konwersji między typami wewnętrznymi i zewnętrznymi reprezentacji znaków.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który może obsłużyć jako zestaw [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class), do kontrolowania konwersji między sekwencją wartości typu *CharType* i sekwencją wartości typu *Byte*. Klasa *StateType* charakteryzuje transformację--i obiekt klasy StateType przechowuje  wszystkie niezbędne informacje o stanie podczas konwersji.

Kodowanie wewnętrzne używa reprezentacji ze stałą liczbą bajtów na znak, zwykle jest to typ **char** lub type **wchar_t**.

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych `id` obiekt statyczny ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią `id`w.

Wersje szablonu [do_in](#do_in) i [do_out](#do_out) zawsze zwracają `codecvt_base::noconv`.

C++ Standardowa biblioteka definiuje kilka jawnych specjalizacji:

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

Konwertuje między **wchar_t** i sekwencjami **znaków** .

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

Konwertuje sekwencje kodowane jako UTF-16 i sekwencje znaków kodowane jako UTF-8.  `char16_t`

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

Konwertuje sekwencje kodowane jako UTF-32 (UCS-4) i sekwencje znaków kodowane jako UTF-8.  `char32_t`

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[codecvt](#codecvt)|Konstruktor dla obiektów klasy `codecvt` , który służy jako zestaw reguł ustawień regionalnych do obsługi konwersji.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[extern_type](#extern_type)|Typ znaku, który jest używany dla zewnętrznych reprezentacji.|
|[intern_type](#intern_type)|Typ znaku, który jest używany dla wewnętrznych reprezentacji.|
|[state_type](#state_type)|Typ znaku, który jest używany do reprezentowania pośrednich stanów w czasie konwersji między wewnętrznymi i zewnętrznymi reprezentacjami.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[always_noconv](#always_noconv)|Sprawdza, czy nie trzeba wykonać żadnych konwersji.|
|[do_always_noconv](#do_always_noconv)|Funkcja wirtualna wywoływana w celu sprawdzenia, czy nie trzeba wykonywać żadnych konwersji.|
|[do_encoding](#do_encoding)|Funkcja wirtualna, która sprawdza, czy kodowanie `Byte` strumienia jest zależne od stanu, czy stosunek `Byte`między używanymi a `CharType`produkowanymi elementami jest stała, a jeśli tak, określa wartość tego stosunku.|
|[do_in](#do_in)|Funkcja wirtualna wywoływana w celu przekonwertowania sekwencji wewnętrznych `Byte`s na sekwencję zewnętrznych `CharType`s.|
|[do_length](#do_length)|Funkcja wirtualna, która określa, ile `Byte`s z danej sekwencji zewnętrznych `Byte`nie produkuje więcej niż określoną liczbę wewnętrznych `CharType`s i zwraca tę liczbę `Byte`.|
|[do_max_length](#do_max_length)|Funkcja wirtualna, która zwraca maksymalną liczbę zewnętrznych bajtów potrzebnych do utworzenia jednej wewnętrznej `CharType`.|
|[do_out](#do_out)|Funkcja wirtualna wywoływana w celu przekonwertowania sekwencji wewnętrznych `CharType`s na sekwencję zewnętrznych bajtów.|
|[do_unshift](#do_unshift)|Funkcja wirtualna wywoływana w celu zapewnienia `Byte`s wymaganych w konwersji zależnej od stanu, aby zakończyć ostatni znak w `Byte`sekwencji s.|
|[Kody](#encoding)|Testuje, czy kodowanie `Byte` strumienia jest zależne od stanu, czy stosunek `Byte`między używanymi a `CharType`produkowanymi elementami jest stała, a jeśli tak, określa wartość tego stosunku.|
|[in](#in)|Konwertuje zewnętrzną reprezentację sekwencji `Byte`s do wewnętrznej reprezentacji `CharType`sekwencji s.|
|[length](#length)|Określa, ile `Byte`s z danej sekwencji zewnętrznych `Byte`nie produkuje więcej niż określoną liczbę wewnętrznych `CharType`s i zwraca tę liczbę `Byte`.|
|[max_length](#max_length)|Zwraca maksymalną liczbę zewnętrznych `Byte`elementów wymaganych do utworzenia jednej wewnętrznej. `CharType`|
|[out](#out)|Konwertuje sekwencję wewnętrznych `CharType`s na sekwencję zewnętrznych `Byte`s.|
|[unshift](#unshift)|Zapewnia zewnętrzne `Byte`s wymagane w konwersji zależnej od stanu, aby zakończyć ostatni znak w `Byte`sekwencji s.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="always_noconv"></a>codecvt:: always_noconv

Sprawdza, czy nie trzeba wykonać żadnych konwersji.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna **prawda** , jeśli nie trzeba wykonywać konwersji; należy wykonać co najmniej jedną **wartość false** .

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_always_noconv](#do_always_noconv).

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

## <a name="codecvt"></a>codecvt:: codecvt

Konstruktor dla obiektów klasy codecvt, który służy jako zestaw reguł ustawień regionalnych do obsługi konwersji.

```cpp
explicit codecvt(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Wartość całkowita służąca do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie są następujące:

- 0: Okres istnienia obiektu jest zarządzany przez elementy lokalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- 2: Te wartości nie są zdefiniowane.

Konstruktor inicjuje swój `locale::facet` obiekt podstawowy przy użyciu **ustawień regionalnych::** [facet](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="do_always_noconv"></a>codecvt::d o_always_noconv

Funkcja wirtualna wywoływana w celu sprawdzenia, czy nie trzeba wykonywać żadnych konwersji.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Chroniona funkcja wirtualna elementu członkowskiego zwraca **wartość true** tylko wtedy, gdy [](#do_out) każde wywołanie `noconv`metody [do_in](#do_in) lub do_out zwraca ciąg.

Wersja szablonu zawsze zwraca **wartość true**.

### <a name="example"></a>Przykład

Zobacz przykład dla [always_noconv](#always_noconv), który wywołuje `do_always_noconv`.

## <a name="do_encoding"></a>codecvt::d o_encoding

Funkcja wirtualna, która sprawdza, czy kodowanie `Byte` strumienia jest zależne od stanu, czy stosunek `Byte`między używanymi a `CharType`produkowanymi elementami jest stała i, jeśli tak, określa wartość tego stosunku.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Chroniona funkcja wirtualna elementu członkowskiego zwraca:

- -1, Jeśli kodowanie sekwencji typu `extern_type` jest zależne od stanu.

- 0, Jeśli kodowanie obejmuje sekwencje o różnej długości.

- *N*, Jeśli kodowanie obejmuje tylko sekwencje o długości *N*

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [kodowania](#encoding), `do_encoding`które wywołuje.

## <a name="do_in"></a>codecvt::d o_in

Funkcja wirtualna wywoływana w celu przekonwertowania sekwencji zewnętrznych `Byte`s na sekwencję wewnętrznych `CharType`s.

```cpp
virtual result do_in(
    StateType& _State,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parametry

*_State*\
Stan konwersji, który jest obsługiwany między wywołaniami funkcji składowej.

*first1*\
Wskaźnik na początek sekwencji do przekonwertowania.

*last1*\
Wskaźnik na koniec sekwencji do przekonwertowania.

*next1*\
Wskaźnik poza końcem skonwertowanej sekwencji do pierwszego nieskonwertowanego znaku.

*first2*\
Wskaźnik na początek skonwertowanej sekwencji.

*last2*\
Wskaźnik na koniec przekonwertowanej sekwencji.

*next2*\
Wskaźnik do `CharType` obiektu, który znajduje się po ostatniej `CharType`konwersji, do pierwszego niezmienionego znaku w sekwencji docelowej.

### <a name="return-value"></a>Wartość zwracana

Zwraca, który wskazuje powodzenie, częściowe powodzenie lub niepowodzenie operacji. Funkcja zwraca:

- `codecvt_base::error`Jeśli sekwencja źródłowa jest źle sformułowana.

- `codecvt_base::noconv`Jeśli funkcja nie wykonuje konwersji.

- `codecvt_base::ok`Jeśli konwersja zakończy się pomyślnie.

- `codecvt_base::partial`Jeśli źródło jest niewystarczające lub miejsce docelowe nie jest wystarczająco duże, aby konwersja powiodła się.

### <a name="remarks"></a>Uwagi

*_State* musi reprezentować początkowy stan konwersji na początku nowej sekwencji źródłowej. Funkcja zmienia wartość przechowywaną w miarę potrzeby, aby odzwierciedlić bieżący stan pomyślnej konwersji. Jego przechowywana wartość jest w inny sposób nieokreślony.

### <a name="example"></a>Przykład

Zobacz przykład dla [programu w programie](#in), który `do_in`wywołuje.

## <a name="do_length"></a>codecvt::d o_length

Funkcja wirtualna, która określa, ile `Byte`s z danej sekwencji zewnętrznych `Byte`nie produkuje więcej niż określoną liczbę wewnętrznych `CharType`s i zwraca tę liczbę `Byte`.

```cpp
virtual int do_length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>Parametry

*_State*\
Stan konwersji, który jest obsługiwany między wywołaniami funkcji składowej.

*first1*\
Wskaźnik na początek sekwencji zewnętrznej.

*last1*\
Wskaźnik na koniec sekwencji zewnętrznej.

*_Len2*\
Maksymalna liczba `Byte`s, które mogą zostać zwrócone przez funkcję składową.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita reprezentująca liczbę konwersji, nie większą niż *_Len2*, zdefiniowanej przez zewnętrzną sekwencję źródłową w [ `first1`, `last1`).

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego `do_in`skutecznie `_State`wywołuje `first1`( `last1` `next1` `_Buf` ,,`_Buf` ,,,`_Len2`, )`next2`dla _  +   *Stan* (kopia stanu), bufor `_Buf`i wskaźniki. `next1` `next2`

Następnie zwraca wartość `next2`.  -  `buf` W związku z tym zlicza maksymalną liczbę konwersji, nie większą niż *_Len2*, zdefiniowane przez sekwencję źródłową w [ `first1`, `last1`).

Wersja szablonu zawsze zwraca część *last1* - *FIRST1* i *_Len2*.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [długości](#length), `do_length`która wywołuje.

## <a name="do_max_length"></a>codecvt::d o_max_length

Funkcja wirtualna, która zwraca maksymalną liczbę zewnętrznych `Byte`elementów wymaganych do utworzenia jednej wewnętrznej. `CharType`

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba elementów `Byte`wymaganych do utworzenia jednego `CharType`.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego zwraca największą dopuszczalną wartość, która [](#do_length)może zostać `first1`zwrócona przez do_length (, `last1`, 1) dla dowolnych prawidłowych wartości *FIRST1* i *last1*.

### <a name="example"></a>Przykład

Zobacz przykład dla [max_length](#max_length), który wywołuje `do_max_length`.

## <a name="do_out"></a>codecvt::d o_out

Funkcja wirtualna wywoływana w celu przekonwertowania sekwencji wewnętrznych `CharType`s na sekwencję zewnętrznych `Byte`s.

```cpp
virtual result do_out(
    StateType& _State,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_State*\
Stan konwersji, który jest obsługiwany między wywołaniami funkcji składowej.

*first1*\
Wskaźnik na początek sekwencji do przekonwertowania.

*last1*\
Wskaźnik na koniec sekwencji do przekonwertowania.

*next1*\
Odwołanie do wskaźnika do pierwszej nieskonwertowanej konwersji `CharType`po ostatniej `CharType` konwersji.

*first2*\
Wskaźnik na początek skonwertowanej sekwencji.

*last2*\
Wskaźnik na koniec przekonwertowanej sekwencji.

*next2*\
Odwołanie do wskaźnika do pierwszej nieskonwertowanej konwersji `Byte`po ostatniej `Byte` konwersji.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca:

- `codecvt_base::error`Jeśli sekwencja źródłowa jest źle sformułowana.

- `codecvt_base::noconv`Jeśli funkcja nie wykonuje konwersji.

- `codecvt_base::ok`Jeśli konwersja zakończy się pomyślnie.

- `codecvt_base::partial`Jeśli źródło jest niewystarczające lub miejsce docelowe nie jest wystarczająco duże, aby konwersja powiodła się.

### <a name="remarks"></a>Uwagi

*_State* musi reprezentować początkowy stan konwersji na początku nowej sekwencji źródłowej. Funkcja zmienia wartość przechowywaną w miarę potrzeby, aby odzwierciedlić bieżący stan pomyślnej konwersji. Jego przechowywana wartość jest w inny sposób nieokreślony.

### <a name="example"></a>Przykład

Zapoznaj się z [przykładem,](#out)który `do_out`wywołuje.

## <a name="do_unshift"></a>codecvt::d o_unshift

Funkcja wirtualna wywoływana w celu zapewnienia `Byte`s wymaganych w konwersji zależnej od stanu, aby zakończyć ostatni znak w `Byte`sekwencji s.

```cpp
virtual result do_unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_State*\
Stan konwersji, który jest obsługiwany między wywołaniami funkcji składowej.

*first2*\
Wskaźnik do pierwszej pozycji w zakresie docelowym.

*last2*\
Wskaźnik do ostatniej pozycji w zakresie docelowym.

*next2*\
Wskaźnik do pierwszego niezmienionego elementu w sekwencji docelowej.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca:

- `codecvt_base::error`Jeśli _ *stanie* reprezentuje nieprawidłowy stan

- `codecvt_base::noconv`Jeśli funkcja nie wykonuje konwersji

- `codecvt_base::ok`Jeśli konwersja zakończy się pomyślnie

- `codecvt_base::partial`Jeśli miejsce docelowe nie jest wystarczająco duże, aby konwersja powiodła się

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego próbuje skonwertować element `CharType`źródłowy (0) na sekwencję docelową, która `first2`jest `last2`przechowywana w [,), z `Byte`wyjątkiem elementu kończącego (0). Zawsze przechowuje w *Next2* wskaźnik do pierwszego niezmienionego elementu w sekwencji docelowej.

_ *Stan* musi reprezentować początkowy stan konwersji na początku nowej sekwencji źródłowej. Funkcja zmienia wartość przechowywaną w miarę potrzeby, aby odzwierciedlić bieżący stan pomyślnej konwersji. Zazwyczaj konwersja elementu `CharType`źródłowego (0) pozostawia bieżący stan w początkowym stanie konwersji.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [zmiany](#unshift), `do_unshift`która wywołuje.

## <a name="encoding"></a>codecvt:: Encoding

Testuje, czy kodowanie `Byte` strumienia jest zależne od stanu, czy stosunek `Byte`między używanymi a `CharType`produkowanymi elementami jest stała, a jeśli tak, określa wartość tego stosunku.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracana jest dodatnia, to jest to stała liczba `Byte` znaków wymagana do `CharType` utworzenia znaku.

Chroniona funkcja wirtualna elementu członkowskiego zwraca:

- -1, Jeśli kodowanie sekwencji typu `extern_type` jest zależne od stanu.

- 0, Jeśli kodowanie obejmuje sekwencje o różnej długości.

- *N*, Jeśli kodowanie obejmuje tylko sekwencje o długości *N.*

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_encoding](#do_encoding).

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

## <a name="extern_type"></a>codecvt:: extern_type

Typ znaku, który jest używany dla zewnętrznych reprezentacji.

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru `Byte`szablonu.

## <a name="in"></a>codecvt:: in

Konwertuje zewnętrzną reprezentację sekwencji `Byte`s do wewnętrznej reprezentacji `CharType`sekwencji s.

```cpp
result in(
    StateType& _State,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parametry

*_State*\
Stan konwersji, który jest obsługiwany między wywołaniami funkcji składowej.

*first1*\
Wskaźnik na początek sekwencji do przekonwertowania.

*last1*\
Wskaźnik na koniec sekwencji do przekonwertowania.

*next1*\
Wskaźnik poza końcem skonwertowanej sekwencji do pierwszego nieskonwertowanego znaku.

*first2*\
Wskaźnik na początek skonwertowanej sekwencji.

*last2*\
Wskaźnik na koniec przekonwertowanej sekwencji.

*next2*\
Wskaźnik do `CharType` obiektu, który znajduje się po ostatnim `Chartype` przekonwertowaniu na pierwszy niezmieniony znak w sekwencji docelowej.

### <a name="return-value"></a>Wartość zwracana

Zwraca, który wskazuje powodzenie, częściowe powodzenie lub niepowodzenie operacji. Funkcja zwraca:

- `codecvt_base::error`Jeśli sekwencja źródłowa jest źle sformułowana.

- `codecvt_base::noconv`Jeśli funkcja nie wykonuje konwersji.

- `codecvt_base::ok`Jeśli konwersja zakończy się pomyślnie.

- `codecvt_base::partial`Jeśli źródło jest niewystarczające lub miejsce docelowe nie jest wystarczająco duże, aby konwersja powiodła się.

### <a name="remarks"></a>Uwagi

*_State* musi reprezentować początkowy stan konwersji na początku nowej sekwencji źródłowej. Funkcja zmienia wartość przechowywanej w razie potrzeby, aby odzwierciedlić bieżący stan pomyślnej konwersji. Po przeprowadzeniu częściowej konwersji *_State* musi być ustawiona tak, aby można było wznowić konwersję po nadejściu nowych znaków.

Funkcja członkowska zwraca [do_in](#do_in)( `_State`, _ *First1, last1, next1, First2, _Llast2, Next2*).

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

## <a name="intern_type"></a>codecvt:: intern_type

Typ znaku, który jest używany dla wewnętrznych reprezentacji.

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru `CharType`szablonu.

## <a name="length"></a>codecvt:: length

Określa, ile `Byte`s z danej sekwencji zewnętrznych `Byte`nie produkuje więcej niż określoną liczbę wewnętrznych `CharType`s i zwraca tę liczbę `Byte`.

```cpp
int length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>Parametry

*_State*\
Stan konwersji, który jest obsługiwany między wywołaniami funkcji składowej.

*first1*\
Wskaźnik na początek sekwencji zewnętrznej.

*last1*\
Wskaźnik na koniec sekwencji zewnętrznej.

*_Len2*\
Maksymalna liczba bajtów, które mogą zostać zwrócone przez funkcję składową.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita reprezentująca liczbę konwersji, nie większą niż *_Len2*, zdefiniowanej przez zewnętrzną sekwencję źródłową w [ `first1`, `last1`).

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_length](#do_length)( *_State, FIRST1*, `last1`, `_Len2`).

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

## <a name="max_length"></a>codecvt:: max_length

Zwraca maksymalną liczbę zewnętrznych `Byte`elementów wymaganych do utworzenia jednej wewnętrznej. `CharType`

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba elementów `Byte`wymaganych do utworzenia jednego `CharType`.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_max_length](#do_max_length).

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

## <a name="out"></a>codecvt:: out

Konwertuje sekwencję wewnętrznych `CharType`s na sekwencję zewnętrznych `Byte`s.

```cpp
result out(
    StateType& _State,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_State*\
Stan konwersji, który jest obsługiwany między wywołaniami funkcji składowej.

*first1*\
Wskaźnik na początek sekwencji do przekonwertowania.

*last1*\
Wskaźnik na koniec sekwencji do przekonwertowania.

*next1*\
Odwołanie do wskaźnika do pierwszej nieskonwertowanej konwersji `CharType` po ostatniej `CharType` konwersji.

*first2*\
Wskaźnik na początek skonwertowanej sekwencji.

*last2*\
Wskaźnik na koniec przekonwertowanej sekwencji.

*next2*\
Odwołanie do wskaźnika do pierwszej nieskonwertowanej konwersji `Byte` po ostatniej konwersji. `Byte`

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca [do_out](#do_out)( `_State` `first1` `last1` `next1` ,,`last2`,,, ,`next2`). `first2`

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [codecvt::d o_out](#do_out).

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

## <a name="state_type"></a>codecvt:: state_type

Typ znaku, który jest używany do reprezentowania pośrednich stanów w czasie konwersji między wewnętrznymi i zewnętrznymi reprezentacjami.

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru `StateType`szablonu.

## <a name="unshift"></a>codecvt:: unshift

Zapewnia s wymagany w konwersji zależnej od stanu, aby zakończyć ostatni znak w `Byte`sekwencji s. `Byte`

```cpp
result unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_State*\
Stan konwersji, który jest obsługiwany między wywołaniami funkcji składowej.

*first2*\
Wskaźnik do pierwszej pozycji w zakresie docelowym.

*last2*\
Wskaźnik do ostatniej pozycji w zakresie docelowym.

*next2*\
Wskaźnik do pierwszego niezmienionego elementu w sekwencji docelowej.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca:

- `codecvt_base::error`Jeśli stan reprezentuje nieprawidłowy stan.

- `codecvt_base::noconv`Jeśli funkcja nie wykonuje konwersji.

- `codecvt_base::ok`Jeśli konwersja zakończy się pomyślnie.

- `codecvt_base::partial`Jeśli miejsce docelowe nie jest wystarczająco duże, aby konwersja powiodła się.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego próbuje skonwertować element `CharType`źródłowy (0) na sekwencję docelową, która `first2`jest `last2`przechowywana w [,), z `Byte`wyjątkiem elementu kończącego (0). Zawsze przechowuje w *Next2* wskaźnik do pierwszego niezmienionego elementu w sekwencji docelowej.

*_State* musi reprezentować początkowy stan konwersji na początku nowej sekwencji źródłowej. Funkcja zmienia wartość przechowywanej w razie potrzeby, aby odzwierciedlić bieżący stan pomyślnej konwersji. Zazwyczaj konwersja elementu `CharType`źródłowego (0) pozostawia bieżący stan w początkowym stanie konwersji.

Funkcja członkowska zwraca [do_unshift](#do_unshift)( `_State`, `first2`, `last2` `next2` ,).

## <a name="see-also"></a>Zobacz także

[\<locale>](../standard-library/locale.md)\
[Strony kodowe](../c-runtime-library/code-pages.md)\
[Nazwy lokalne, Języki i ciągi kraj/region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

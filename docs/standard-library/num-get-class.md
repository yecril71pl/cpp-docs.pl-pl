---
title: num_get — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
ms.openlocfilehash: 67aef1ce52b6717ce6d6381429982cf660aa5e20
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457643"
---
# <a name="numget-class"></a>num_get — Klasa

Klasa szablonu opisująca obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu `CharType` na wartości liczbowe.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

*InputIterator*\
Typ iteratora, z którego liczbowe funkcje get odczytują swoje dane wejściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[num_get](#num_get)|Konstruktor dla obiektów typu `num_get` , które są używane do wyodrębniania wartości liczbowych z sekwencji.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wejściowych.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[do_get](#do_get)|Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej lub logicznej z sekwencji znaków.|
|[get](#get)|Wyodrębnia wartość liczbową lub logiczną z sekwencji znaków.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="char_type"></a>num_get::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu CharType .

## <a name="do_get"></a>num_get::d o_get

Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej lub logicznej z sekwencji znaków.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Początek zakresu znaków, z którego ma zostać odczytana liczba.

*ostatniego*\
Koniec zakresu znaków, z którego ma zostać odczytana liczba.

*_Iosbase*\
[Ios_base](../standard-library/ios-base-class.md) , którego flagi są używane przez konwersję.

*_State*\
Stan, do którego failbit (zobacz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate)) jest dodawany w przypadku awarii.

*użyte*\
Wartość, która została odczytana.

### <a name="return-value"></a>Wartość zwracana

Iterator po odczytaniu wartości.

### <a name="remarks"></a>Uwagi

Pierwsza wirtualna chroniona funkcja członkowska,

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
```

dopasowuje elementy sekwencyjne  zaczynające się na `[first, last)` pierwszy dzień w sekwencji, dopóki nie rozpoznano kompletnego, niepustego pola wejściowego liczby całkowitej. Jeśli to się powiedzie, konwertuje to pole na jego równoważną wartość jako typ **Long**i zapisuje wynik w wartości *Val*. Zwraca iterator wyznaczający pierwszy element poza liczbowe pole wejściowe. W przeciwnym razie funkcja przechowuje Nothing w wartości *Val* i `ios_base::failbit` ustawia `state`w. Zwraca iterator wyznaczający pierwszy element poza dowolnym prefiksem prawidłowego pola wejściowego Integer. W obu przypadkach, jeśli wartość zwracana jest równa `last`, funkcja ustawia `ios_base::eofbit` w. `state`

Pole danych wejściowych Integer jest konwertowane na te same reguły, które są używane przez funkcje skanowania do dopasowywania i konwertowania serii elementów **char** z pliku. (Każdy taki **znak** jest założono, że jest mapowany na odpowiednik elementu typu `Elem` przez proste, jeden do jednego, mapowanie.) Zgodna specyfikacja konwersji skanowania jest określana w następujący sposób:

Jeśli `iosbase.` [ios_base:: flage](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[OCT](../standard-library/ios-functions.md#oct), specyfikacja konwersji to `lo`.

W `iosbase.flags() & ios_base::basefield == ios_base::`przypadku [znaków szesnastkowych](../standard-library/ios-functions.md#hex)specyfikacja konwersji `lx`to.

Jeśli `iosbase.flags() & ios_base::basefield == 0`jest, specyfikacja konwersji to `li`.

W przeciwnym razie specyfikacja konwersji to `ld`.

Format pola wejściowego Integer jest bardziej`fac` określony przez zestaw [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class) zwrócony przez wywołanie [use_facet](../standard-library/locale-functions.md#use_facet) `<` [numpunct](../standard-library/numpunct-class.md) `<Elem>(iosbase.` [ios_base:: getloc](../standard-library/ios-base-class.md#getloc)`())`. Opracowany

`fac.`[numpunct:: Grouping](../standard-library/numpunct-class.md#grouping) `()` określa sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego.

`fac.`[numpunct:: thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` Określa sekwencję oddzielającą grupy cyfr po lewej stronie dowolnego miejsca dziesiętnego.

Jeśli w polu numeryczne dane wejściowe nie `fac.thousands_sep()` występują wystąpienia wystąpień, nie zostanie nałożone ograniczenie grupowania. W przeciwnym razie wszystkie ograniczenia grupowania narzucone przez `fac.grouping()` są wymuszane, a separatory zostaną usunięte przed wykonaniem konwersji skanowania.

Czwarta chroniona funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że zastępuje specyfikację `ld` konwersji `lu`z. Jeśli to się powiedzie, konwertuje pole numeryczne na wartość typu **unsigned long** i zapisuje tę wartość w *Val*.

Piąta chroniona funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że zastępuje specyfikację `ld` konwersji `lld`z. Jeśli to się powiedzie, konwertuje pole numeryczne na wartość typu **Long Long** i zapisuje tę wartość w *Val*.

Szósta chroniona funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że zastępuje specyfikację `ld` konwersji `llu`z. W przypadku pomyślnego przekonwertowania pola dane wejściowe na wartość typu unsigned long **Long** i zapisuje tę wartość w *Val*.

Siódma wirtualna chroniona funkcja członkowska:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że przedsięwzięciach się na wypełnienie kompletnego, niepustego pola wejściowego zmiennoprzecinkowego. `fac.`[numpunct::d ecimal_point](../standard-library/numpunct-class.md#decimal_point) `()` Określa sekwencję oddzielające cyfry całkowite od cyfr ułamkowych. Odpowiednik specyfikatora przeliczeniowego skanowania `lf`to.

Ósma wirtualna chroniona funkcja członkowska:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że przedsięwzięciach się na wypełnienie kompletnego, niepustego pola wejściowego zmiennoprzecinkowego. `fac.`[numpunct::d ecimal_point](../standard-library/numpunct-class.md#decimal_point) `()` Określa sekwencję oddzielające cyfry całkowite od cyfr ułamkowych. Odpowiednik specyfikatora przeliczeniowego skanowania `lf`to.

Dziewiąta chroniona funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

zachowuje się tak samo, jak osiem, z tą różnicą, że równoważnego specyfikatora konwersji skanowania jest `Lf`.

Dziesiąta chroniona funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

zachowuje się tak samo, z tą różnicą, że równoważnego specyfikatora konwersji `p`skanowania jest.

Ostatnia (jedenasta) wirtualna funkcja chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że przedsięwzięciach się na wypełnienie kompletnego, niepustego pola wejściowego Boolean. W przypadku pomyślnego przeprowadzenia konwersji pola danych wejściowych Boolean na wartość typu **bool** i przechowuje tę wartość w *Val*.

Pole danych wejściowych Boolean przyjmuje jeden z dwóch form. Jeśli `iosbase.flags() & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) ma wartość false, jest taka sama jak pole danych wejściowych Integer, z tą różnicą, że przekonwertowana wartość musi być równa 0 (dla wartości false) lub 1 (dla prawdy). W przeciwnym razie sekwencja musi być zgodna `fac.`z`()` [numpunct:: falsename](../standard-library/numpunct-class.md#falsename) (dla false) lub `fac.` [numpunct:: TrueName](../standard-library/numpunct-class.md#truename) `()` (dla prawdy).

### <a name="example"></a>Przykład

Zobacz przykład dla [Get](#get), gdzie wirtualna funkcja członkowska jest wywoływana przez `do_get`.

## <a name="get"></a>num_get:: Get

Wyodrębnia wartość liczbową lub logiczną z sekwencji znaków.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Początek zakresu znaków, z którego ma zostać odczytana liczba.

*ostatniego*\
Koniec zakresu znaków, z którego ma zostać odczytana liczba.

*_Iosbase*\
[Ios_base](../standard-library/ios-base-class.md) , którego flagi są używane przez konwersję.

*_State*\
Stan, do którego failbit (zobacz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate)) jest dodawany w przypadku awarii.

*użyte*\
Wartość, która została odczytana.

### <a name="return-value"></a>Wartość zwracana

Iterator po odczytaniu wartości.

### <a name="remarks"></a>Uwagi

Wszystkie funkcje składowe [](#do_get)zwracają do_get `first`( `last` `_Iosbase` `_State`,,,, ).`val`

Pierwsza wirtualna chroniona funkcja członkowska próbuje dopasować elementy sekwencyjne zaczynające się od pierwszej `first`w `last`sekwencji [,), dopóki nie rozpoznano kompletnego, niepustego pola wejściowego. Jeśli to się powiedzie, konwertuje to pole na jego równoważną wartość jako typ **Long** i zapisuje wynik w wartości *Val*. Zwraca iterator wyznaczający pierwszy element poza liczbowe pole wejściowe. W przeciwnym razie funkcja przechowuje Nothing w wartości *Val* i `ios_base::failbit` ustawia w *stanie*_. Zwraca iterator wyznaczający pierwszy element poza dowolnym prefiksem prawidłowego pola wejściowego Integer. W obu przypadkach, jeśli wartość zwracana jest równa *Last*, funkcja ustawia `ios_base::eofbit` się w *_State*.

Pole danych wejściowych Integer jest konwertowane na te same reguły, które są używane przez funkcje skanowania do dopasowywania i konwertowania serii elementów **char** z pliku. Każdy taki **znak** jest założono, że jest mapowany na odpowiednik elementu typu `CharType` przez proste, jedno-do-jednego mapowania. Zgodna specyfikacja konwersji skanowania jest określana w następujący sposób:

- If `iosbase`. [flagami](../standard-library/ios-base-class.md#flags) & dlaKTZ`ios_base::basefield`, specyfikacja konwersji[](../standard-library/ios-functions.md#oct)to .`lo` == `ios_base::`

- Jeśli **iosbase. flags** & **ios_base:: basefield** == `ios_base::`[HEX](../standard-library/ios-functions.md#hex), specyfikacja konwersji to `lx`.

- Jeśli **iosbase. flags** & **ios_base:: basefield** = = 0, specyfikacja konwersji to `li`.

- W przeciwnym razie specyfikacja konwersji to `ld`.

Format pola wejściowego Integer jest bardziej określony przez zestaw [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class)**FAC** zwrócony przez wywołanie [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md) \< **elem**> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). Opracowany

- **FAC**. [grupowanie](../standard-library/numpunct-class.md#grouping) określa sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego.

- **FAC**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) Określa sekwencję, która oddziela grupy cyfr po lewej stronie dowolnego miejsca dziesiętnego.

Jeśli nie ma wystąpień elementu **FAC**. `thousands_sep`występuje w polu liczbowych danych wejściowych, nie jest nakładane ograniczenie grupowania. W przeciwnym razie wszystkie ograniczenia grupowania narzucone przez **FAC**. **grupowanie** jest wymuszane, a separatory są usuwane przed wykonaniem konwersji skanowania.

Druga wirtualna chroniona funkcja członkowska:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że zastępuje specyfikację `ld` konwersji `lu`z. Jeśli to się powiedzie, konwertuje pole liczbowe dane wejściowe na wartość typu **unsigned long** i zapisuje tę wartość w *Val*.

Trzecia wirtualna chroniona funkcja członkowska:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że próbuje dopasować kompletne, niepuste pole wejściowe zmiennoprzecinkowe. **FAC**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) Określa sekwencję oddzielające cyfry całkowite od cyfr ułamkowych. Odpowiednik specyfikatora przeliczeniowego skanowania `lf`to.

Czwarta chroniona funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

zachowuje się tak samo trzeci, z tą różnicą, że równoważny specyfikator `Lf`przeliczeniowego skanowania.

Piąta chroniona funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

zachowuje się tak samo, z tą różnicą, że równoważnego specyfikatora konwersji `p`skanowania jest.

Szósta chroniona funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że próbuje dopasować kompletne, niepuste pole wejściowej wartości logicznej. W przypadku pomyślnego przeprowadzenia konwersji pola danych wejściowych Boolean na wartość typu **bool** i przechowuje tę wartość w *Val*.

Pole danych wejściowych Boolean przyjmuje jeden z dwóch form. Jeśli **iosbase**. **flagi** [](../standard-library/ios-functions.md#boolalpha)  boolalpha ma wartość false, jest taka sama jak pole danych wejściowych Integer, z tą różnicą, że przekonwertowana wartość musi być równa 0 (dla wartości false) lub 1 (dla prawdy). & `ios_base::` W przeciwnym razie sekwencja musi być zgodna z **FAC**. [wartość falsename](../standard-library/numpunct-class.md#falsename) (w przypadku **wartości false**) lub **FAC**. [wartość TrueName](../standard-library/numpunct-class.md#truename) (w przypadku **wartości true**).

### <a name="example"></a>Przykład

```cpp
// num_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   basic_stringstream<char> psz, psz2;
   psz << "-1000,56";

   ios_base::iostate st = 0;
   long double fVal;
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;

   psz.imbue( loc );
   use_facet <num_get <char> >
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter(0), psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get( ) FAILED" << endl;
   else
      cout << "money_get( ) = " << fVal << endl;
}
```

## <a name="iter_type"></a>num_get::iter_type

Typ, który opisuje iterator danych wejściowych.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru `InputIterator`szablonu.

## <a name="num_get"></a>num_get::num_get

Konstruktor dla obiektów typu `num_get` , które są używane do wyodrębniania wartości liczbowych z sekwencji.

```cpp
explicit num_get(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Wartość całkowita służąca do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie są następujące:

- 0: Okres istnienia obiektu jest zarządzany przez elementy lokalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- \> 1: Te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój obiekt podstawowy przy użyciu **ustawień regionalnych::** [facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="see-also"></a>Zobacz także

[\<locale>](../standard-library/locale.md)\
[facet — Klasa](../standard-library/locale-class.md#facet_class)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

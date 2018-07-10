---
title: money_get — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/std::money_get
- xlocmon/std::money_get::char_type
- xlocmon/std::money_get::iter_type
- xlocmon/std::money_get::string_type
- xlocmon/std::money_get::do_get
- xlocmon/std::money_get::get
dev_langs:
- C++
helpviewer_keywords:
- std::money_get [C++]
- std::money_get [C++], char_type
- std::money_get [C++], iter_type
- std::money_get [C++], string_type
- std::money_get [C++], do_get
- std::money_get [C++], get
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e3059a4291d21e11304fdf571d2e12828df26fb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861704"
---
# <a name="moneyget-class"></a>money_get — Klasa

Klasa szablonu opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do sterowania konwersje sekwencji typu `CharType` do wartości monetarnych.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

`CharType` Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

`InputIterator` Typ iteratora, z którego funkcje get odczytu danych wejściowych.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba jej wartości przechowywanej dostępu są przechowywane w unikatową wartość dodatnią **identyfikator.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[money_get](#money_get)|Konstruktor dla obiektów typu `money_get` służące do wyodrębniania wartości liczbowe sekwencji reprezentujący wartości monetarnych.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wejściowych.|
|[string_type](#string_type)|Typ, który opisuje ciąg zawierający znaki typu `CharType`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[do_get](#do_get)|Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej z sekwencji znaków, która reprezentuje wartość pieniężną.|
|[get](#get)|Wyodrębnia wartość liczbową z sekwencji znaków, która reprezentuje wartość pieniężną.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** Standard

## <a name="char_type"></a>  money_get::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

## <a name="do_get"></a>  money_get::do_get

Wywołuje się, by funkcji wirtualnej wyodrębnia wartość liczbową z sekwencja znaków, który reprezentuje wartość pieniężną.

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const
```

### <a name="parameters"></a>Parametry

`first` Wprowadź iteratora adresowania na początku sekwencji do skonwertowania.

`last` Wprowadź iteratora adresowania koniec sekwencji do skonwertowania.

`Intl` Wartość logiczna określająca typ symbolu waluty oczekiwano w sekwencji: **true** Jeśli międzynarodowe, **false** Jeśli krajowego.

`Iosbase` Flaga formatu, który po zestaw oznacza, że symbol waluty jest opcjonalna. w przeciwnym razie jest wymagana.

`State` Ustawia elementy maski odpowiedni stan strumienia w zależności od tego, czy operacje zakończyło się powodzeniem, czy nie.

`val` Ciąg przekonwertowany sekwencji przechowywania.

### <a name="return-value"></a>Wartość zwracana

Wejściowy iteratora adresowania pierwszy element poza pieniężnego pola wejściowego.

### <a name="remarks"></a>Uwagi

Pierwszej funkcji wirtualnych chroniony element członkowski próbuje dopasować sekwencyjnych elementy, rozpoczynając od pierwszego w sekwencji [ `first`, `last`) dopóki nie został rozpoznany kompletna, niepustym pieniężnego wejściowy pola. Jeśli się powiedzie, konwertuje to pole z jednego lub więcej cyfr dziesiętnych, opcjonalnie poprzedzony znakiem minus sekwencji ( `-`), aby oznaczyć i przechowuje wyniki w [string_type](#string_type) obiektu `val`. Zwraca iteratora wyznaczenie pierwszy element poza pieniężnego pola wejściowego. W przeciwnym razie funkcja przechowuje pustej sekwencji w `val` i ustawia `ios_base::failbit` w `State`. Zwraca iteratora wyznaczenie pierwszy element poza dowolnego prefiksu prawidłowy pieniężnego pola wejściowego. W obu przypadkach jest równa wartości zwracanej `last`, zestawy funkcji `ios_base::eofbit` w `State`.

Drugi funkcji wirtualnych chroniony element członkowski działa tak samo jako pierwszy, z wyjątkiem tego, że w przypadku powodzenia sekwencji opcjonalnie podpisanej cyfry są konwertowane na wartość typu `long double` i zapisuje tę wartość w `val`.

Format pieniężnego pola wejściowego jest określany przez [aspektu ustawień regionalnych](../standard-library/locale-class.md#facet_class)**fac** zwrócony przez wywołanie skuteczne [use_facet](../standard-library/locale-functions.md#use_facet)  <  [ moneypunct —](../standard-library/moneypunct-class.md) \< **CharType**, **wewnętrzna**>> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

W szczególności:

- **FAC**. [neg_format](../standard-library/moneypunct-class.md#neg_format) określa kolejność, w którym występuje części pola.

- **FAC**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) określa kolejność elementów, który stanowi symbol waluty.

- **FAC**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) określa kolejność elementów stanowi znak dodatni.

- **FAC**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) określa kolejność elementów stanowi symbolu wartości ujemnej.

- **FAC**. [Grupowanie](../standard-library/moneypunct-class.md#grouping) określa sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego.

- **FAC**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) określa element oddzielający grup cyfr w lewą stronę dowolnego punktu dziesiętnego.

- **FAC**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) określa element oddzielający cyfr liczbą całkowitą od cyfr ułamek.

- **FAC**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) określa liczbę cyfr znaczących ułamek na prawo od dowolnego punktu dziesiętnego. Podczas analizowania kwotę pieniężną więcej cyfr ułamek nie są wymagane przez `frac_digits`, `do_get` zatrzymuje analizowania po użyciu najwyżej `frac_digits` znaków.

Jeśli parametry logowania ( **fac**. `negative_sign` lub **fac**. `positive_sign`) ma więcej niż jeden element, tylko pierwszy element dopasowaniu gdzie element równa **money_base::sign** pojawia się we wzorcu formatu ( **fac**. `neg_format`). Wszystkie pozostałe elementy są dopasowywane w końcu pieniężnego pola wejściowego. Jeśli żaden ciąg ma pierwszy element, który odpowiada następnego elementu w polu wejściowym pieniężnego, parametry logowania są podejmowane jako pusta, i znak jest dodatnia.

Jeśli **iosbase**. [flagi](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) jest różna od zera, ciąg **fac**. `curr_symbol` musi odpowiadać, gdy element równa **money_base::symbol** jest wyświetlana w formacie wzorca. W przeciwnym razie, jeśli **money_base::symbol** występuje na końcu wzorca format, a jeśli pozostają żadnych elementów parametry logowania do dopasowania, symbol waluty nie jest zgodny. W przeciwnym razie opcjonalnie jest takie samo symbol waluty.

Jeśli nie wystąpienia **fac**. `thousands_sep` występują we fragmencie wartości walutowej pole wejściowe (gdzie element równa **money_base::value** pojawia się we wzorcu format), jest nałożone nie ograniczenia grupowania. W przeciwnym razie żadnych ograniczeń grupowania powodowanego przez **fac**. **Grupowanie** jest wymuszana. Należy pamiętać, że wynikowa sekwencja cyfr reprezentuje całkowitą którego znaczącymi **fac**. `frac_digits` cyfr dziesiętnych są traktowane jako z prawej strony punktu dziesiętnego.

Dowolny biały znak jest dopasowywany gdzie element równa **money_base::space** jest dostępna we wzorcu format, w przypadku innych niż wydaje się na końcu wzorca format. W przeciwnym razie nie odpowiada nie wewnętrzny biały znak. Element *ch* jest uznawany za biały znak, jeśli [use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md) \< **CharType**>> () **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). [jest](../standard-library/ctype-class.md#is)( **ctype_base::space**, *ch*) jest **true**.

### <a name="example"></a>Przykład

Zobacz przykład [uzyskać](#get), które wywołuje `do_get`.

## <a name="get"></a>  money_get::Get

Wyodrębnia wartość liczbową z sekwencji znaków, która reprezentuje wartość pieniężną.

```cpp
iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const;

iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const;
```

### <a name="parameters"></a>Parametry

`first` Wprowadź iteratora adresowania na początku sekwencji do skonwertowania.

`last` Wprowadź iteratora adresowania koniec sekwencji do skonwertowania.

`Intl` Wartość logiczna określająca typ symbolu waluty oczekiwano w sekwencji: **true** Jeśli międzynarodowe, **false** Jeśli krajowego.

`Iosbase` Flaga formatu, który po zestaw oznacza, że symbol waluty jest opcjonalna. w przeciwnym razie jest wymagana

`State` Ustawia elementy maski odpowiedni stan strumienia w zależności od tego, czy operacja powiodła się.

`val` Ciąg przekonwertowany sekwencji przechowywania.

### <a name="return-value"></a>Wartość zwracana

Wejściowy iteratora adresowania pierwszy element poza pieniężnego pola wejściowego.

### <a name="remarks"></a>Uwagi

Zarówno funkcje Członkowskie zwracają [do_get](#do_get)`(first, last, Intl, Iosbase, State, val)`.

### <a name="example"></a>Przykład

```cpp
// money_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;

int main( )
{
   locale loc( "german_germany" );

   basic_stringstream< char > psz;
   psz << use_facet<moneypunct<char, 1> >(loc).curr_symbol() << "-1.000,56";
   basic_stringstream< char > psz2;
   psz2 << "-100056" << use_facet<moneypunct<char, 1> >(loc).curr_symbol();

   ios_base::iostate st = 0;
   long double fVal;

   psz.flags( psz.flags( )|ios_base::showbase );
   // Which forced the READING the currency symbol
   psz.imbue(loc);
   use_facet < money_get < char > >( loc ).
      get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter( 0 ), true, psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get(" << psz.str( ) << ", intl = 1) FAILED"
           << endl;
   else
      cout << "money_get(" << psz.str( ) << ", intl = 1) = "
           << fVal/100.0 << endl;

   use_facet < money_get < char > >( loc ).
      get(basic_istream<char>::_Iter(psz2.rdbuf( )),
          basic_istream<char>::_Iter(0), false, psz2, st, fVal);

   if ( st & ios_base::failbit )
      cout << "money_get(" << psz2.str( ) << ", intl = 0) FAILED"
           << endl;
   else
      cout << "money_get(" << psz2.str( ) << ", intl = 0) = "
           << fVal/100.0 << endl;
};
```

## <a name="iter_type"></a>  money_get::iter_type

Typ, który opisuje iterator danych wejściowych.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **InputIterator**.

## <a name="money_get"></a>  money_get::money_get

Konstruktor dla obiektów typu `money_get` służące do wyodrębniania wartości liczbowe sekwencji reprezentujący wartości monetarnych.

```cpp
explicit money_get(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

`_Refs` Wartość całkowita używany do określania typu zarządzania pamięci dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości `_Refs` i ich znaczenie są:

- 0: okres istnienia obiektu zarządza ustawieniami regionalnymi, które zawierałoby proces.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: te wartości są niezdefiniowane.

Nie bezpośredniego przykładów to możliwe, ponieważ destruktor jest chroniony.

Konstruktor inicjuje jego obiektu podstawowego z **locale::**[aspektu](../standard-library/locale-class.md#facet_class)(**_ *** system plików Refs*).

## <a name="string_type"></a>  money_get::STRING_TYPE

Typ, który opisuje ciąg zawierający znaki typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ w tym artykule opisano specjalizacji szablonu klasy [basic_string —](../standard-library/basic-string-class.md).

## <a name="see-also"></a>Zobacz także

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[facet — klasa](../standard-library/locale-class.md#facet_class)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

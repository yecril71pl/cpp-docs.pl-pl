---
title: money_get — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_get
- xlocmon/std::money_get::char_type
- xlocmon/std::money_get::iter_type
- xlocmon/std::money_get::string_type
- xlocmon/std::money_get::do_get
- xlocmon/std::money_get::get
helpviewer_keywords:
- std::money_get [C++]
- std::money_get [C++], char_type
- std::money_get [C++], iter_type
- std::money_get [C++], string_type
- std::money_get [C++], do_get
- std::money_get [C++], get
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
ms.openlocfilehash: eb5e1a7b83db561687f83be96c79add8b54589e8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455557"
---
# <a name="moneyget-class"></a>money_get — Klasa

Klasa szablonu opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu `CharType` na wartości pieniężne.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

*InputIterator*\
Typ iteratora, z której funkcje get odczytują swoje dane wejściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[money_get](#money_get)|Konstruktor dla obiektów typu `money_get` , które są używane do wyodrębniania wartości liczbowych z sekwencji reprezentujących wartości pieniężne.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wejściowych.|
|[string_type](#string_type)|Typ, który opisuje ciąg zawierający znaki typu `CharType`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[do_get](#do_get)|Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej z sekwencji znaków, która reprezentuje wartość pieniężną.|
|[get](#get)|Wyodrębnia wartość liczbową z sekwencji znaków, która reprezentuje wartość pieniężną.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="char_type"></a>money_get::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu CharType .

## <a name="do_get"></a>money_get::d o_get

Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej z sekwencji znaków, która reprezentuje wartość pieniężną.

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

*pierwszego*\
Iterator danych wejściowych odnoszący się do początku sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych odnoszący się do końca sekwencji do przekonwertowania.

*Intl*\
Wartość logiczna wskazująca typ symbolu waluty oczekiwanego w sekwencji: **prawda** , jeśli międzynarodowy, **Fałsz** , jeśli jest w trybie wewnętrznym.

*Iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny. w przeciwnym razie jest to wymagane.

*Państwu*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się powodzeniem, czy nie.

*użyte*\
Ciąg przechowujący przekonwertowaną sekwencję.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu poza walutowym polem wejściowym.

### <a name="remarks"></a>Uwagi

Pierwsza wirtualna chroniona funkcja członkowska próbuje dopasować elementy sekwencyjne zaczynające się od pierwszej `first`w `last`sekwencji [,), dopóki nie rozpoznano kompletnego, niepustego pola wejściowego pieniężnego. Jeśli to się powiedzie, konwertuje to pole na sekwencję jednej lub więcej cyfr dziesiętnych, opcjonalnie poprzedzone znakiem minus `-`(), aby reprezentować wartość i zapisuje wynik w [](#string_type) obiekcie string_type *Val*. Zwraca iterator wyznaczający pierwszy element poza pole danych wejściowych pieniężnych. W przeciwnym razie funkcja przechowuje pustą sekwencję w *Val* i `ios_base::failbit` ustawia w *stanie*. Zwraca iterator wyznaczający pierwszy element poza dowolnym prefiksem prawidłowego pola wejściowego pieniężnego. W obu przypadkach, jeśli wartość zwracana jest równa `last`, funkcja ustawia `ios_base::eofbit` w. `State`

Druga wirtualna chroniona funkcja członkowska zachowuje się tak samo jak pierwszy, z tą różnicą, że w przypadku pomyślnego przekonwertowania opcjonalnej sekwencji cyfr opcjonalnie na wartość typu **Long Double** i zapisuje tę wartość w *Val*.

Format pola danych wejściowych pieniężnych jest określany na podstawie [zestawu reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class)**FAC** zwracanego przez efektywne wywołanie [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **Intl**> > ( **iosbase** . [getloc](../standard-library/ios-base-class.md#getloc)).

Opracowany

- **FAC**. [neg_format](../standard-library/moneypunct-class.md#neg_format) określa kolejność, w jakiej występują składniki pola.

- **FAC**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) Określa sekwencję elementów, które stanowią symbol waluty.

- **FAC**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) Określa sekwencję elementów, które stanowią znak dodatni.

- **FAC**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) Określa sekwencję elementów, które stanowią znak ujemny.

- **FAC**. [grupowanie](../standard-library/moneypunct-class.md#grouping) określa sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego.

- **FAC**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) określa element oddzielający grupy cyfr po lewej stronie dowolnego miejsca dziesiętnego.

- **FAC**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) określa element oddzielający cyfry całkowite od cyfr ułamkowych.

- **FAC**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) określa liczbę znaczących cyfr ułamków po prawej stronie dowolnego punktu dziesiętnego. Podczas analizowania kwoty pieniężnej o większej liczbie ułamków niż jest wywoływana `frac_digits`przez `do_get` , program przerywa analizowanie po użyciu najwyżej `frac_digits` znaków.

Jeśli ciąg znaków ( **FAC**. `negative_sign`lub **FAC**. `positive_sign`) ma więcej niż jeden element, tylko pierwszy element jest dopasowany, gdzie element **money_base:: Sign** jest wyświetlany w wzorcu formatu ( **FAC**. `neg_format`). Wszystkie pozostałe elementy są dopasowywane na końcu pola danych wejściowych pieniężnych. Jeśli żaden z parametrów nie ma pierwszego elementu, który jest zgodny z następnym elementem w polu wejściowym walutowym, ciąg znaków jest traktowany jako pusty, a znak jest dodatni.

Jeśli **iosbase**. [flagi](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) są różna od zera, ciąg **FAC**. `curr_symbol`musi być taka sama, gdzie element **money_base:: symbol** jest wyświetlany w wzorcu formatu. W przeciwnym razie, jeśli **money_base:: symbol** występuje na końcu wzorca formatu i jeśli żadne elementy ciągu znaków nie pozostaną dopasowane, symbol waluty nie jest dopasowany. W przeciwnym razie symbol waluty jest opcjonalnie dopasowany.

Jeśli nie ma wystąpień elementu **FAC**. `thousands_sep`występuje w części wartości pola danych wejściowych pieniężnych (gdzie element **money_base:: value** jest wyświetlany we wzorcu formatowania), nie nałożono ograniczenia grupowania. W przeciwnym razie wszystkie ograniczenia grupowania narzucone przez **FAC**. **grupowanie** jest wymuszane. Należy zauważyć, że wynikiem sekwencji cyfr reprezentuje liczbę całkowitą, której **FAC**o niskiej kolejności. `frac_digits`cyfry dziesiętne są uwzględniane z prawej strony punktu dziesiętnego.

Dowolny biały znak jest dopasowywany w przypadku, gdy element jest równy **money_base:: spacja** pojawia się w wzorcu formatu, jeśli występuje inaczej niż na końcu wzorca formatu. W przeciwnym razie nie jest dopasowywany wewnętrzny odstęp. Element *ch* jest traktowany jako białe miejsce, jeśli [use_facet](../standard-library/locale-functions.md#use_facet) < [CType](../standard-library/ctype-class.md) \< **CharType**> > ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). [jest](../standard-library/ctype-class.md#is) ( **ctype_base:: Space**, *ch*) ma **wartość true**.

### <a name="example"></a>Przykład

Zobacz przykład dla [Get](#get), który wywołuje `do_get`.

## <a name="get"></a>money_get:: Get

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

*pierwszego*\
Iterator danych wejściowych odnoszący się do początku sekwencji do przekonwertowania.

*ostatniego*\
Iterator danych wejściowych odnoszący się do końca sekwencji do przekonwertowania.

*Intl*\
Wartość logiczna wskazująca typ symbolu waluty oczekiwanego w sekwencji: **prawda** , jeśli międzynarodowy, **Fałsz** , jeśli jest w trybie wewnętrznym.

*Iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny. w przeciwnym razie jest to wymagane

*Państwu*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się powodzeniem.

*użyte*\
Ciąg przechowujący przekonwertowaną sekwencję.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu poza walutowym polem wejściowym.

### <a name="remarks"></a>Uwagi

Obie funkcje członkowskie zwracają [do_get](#do_get)`(first, last, Intl, Iosbase, State, val)`.

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

## <a name="iter_type"></a>money_get::iter_type

Typ, który opisuje iterator danych wejściowych.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **InputIterator**.

## <a name="money_get"></a>money_get::money_get

Konstruktor dla obiektów typu `money_get` , które są używane do wyodrębniania wartości liczbowych z sekwencji reprezentujących wartości pieniężne.

```cpp
explicit money_get(size_t _Refs = 0);
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

Konstruktor inicjuje swój obiekt podstawowy przy użyciu **ustawień regionalnych::** [facet](../standard-library/locale-class.md#facet_class)( *_Refs*).

## <a name="string_type"></a>money_get::string_type

Typ, który opisuje ciąg zawierający znaki typu CharType .

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację klasy szablonu [basic_string](../standard-library/basic-string-class.md).

## <a name="see-also"></a>Zobacz także

[\<locale>](../standard-library/locale.md)\
[facet — Klasa](../standard-library/locale-class.md#facet_class)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

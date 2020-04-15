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
ms.openlocfilehash: ac85e99bfb834fd970a804269f25ec9f20960a23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375901"
---
# <a name="money_get-class"></a>money_get — Klasa

Szablon klasy opisuje obiekt, który może służyć jako aspekt ustawień regionalnych `CharType` do kontrolowania konwersji sekwencji typu do wartości pieniężnych.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

*InputIterator*\
Typ iteratora, z której funkcje get odczytują swoje dane wejściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[money_get](#money_get)|Konstruktor obiektów typu, `money_get` które są używane do wyodrębniania wartości liczbowych z sekwencji reprezentujących wartości pieniężne.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wejściowych.|
|[string_type](#string_type)|Typ opisujący ciąg zawierający znaki `CharType`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[do_get](#do_get)|Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej z sekwencji znaków, która reprezentuje wartość pieniężną.|
|[get](#get)|Wyodrębnia wartość liczbową z sekwencji znaków, która reprezentuje wartość pieniężną.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="money_getchar_type"></a><a name="char_type"></a>money_get::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu *CharType*.

## <a name="money_getdo_get"></a><a name="do_get"></a>money_get::do_get

Funkcja wirtualna wywoływana w celu wyodrębnienia wartości liczbowej z sekwencji znaków, która reprezentuje wartość pieniężną.

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

*Pierwszym*\
Iterator wejściowy adresowania początku sekwencji do konwersji.

*Ostatnio*\
Iterator wprowadzania adresowania koniec sekwencji do konwersji.

*Intl*\
Wartość logiczna wskazująca typ symbolu waluty oczekiwany w sekwencji: **true** if international, **false** if domestic.

*Baza Iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny; w przeciwnym razie jest to wymagane.

*Państwa*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się pomyślnie, czy nie.

*Val*\
Ciąg przechowujący przekonwertowane sekwencji.

### <a name="return-value"></a>Wartość zwracana

Iterator wejściowy adresowania pierwszego elementu poza pole wejściowe pieniężne.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja wirtualnego chronionego elementu członkowskiego próbuje dopasować kolejne elementy `first` `last`rozpoczynające się od początku w sekwencji [ , ), dopóki nie rozpozna kompletne, niepusty pieniężne pole wejściowe. Jeśli to się powiedzie, konwertuje to pole na sekwencję jednej lub więcej cyfr `-`dziesiętnych, opcjonalnie poprzedzone znakiem minus ( ), aby reprezentować kwotę i przechowuje wynik w [string_type](#string_type) *val*obiektu . Zwraca iterator wyznaczający pierwszy element poza polem danych wejściowych pieniężnych. W przeciwnym razie funkcja przechowuje pustą sekwencję w *val* i ustawia `ios_base::failbit` w *stanie*. Zwraca iterator wyznaczający pierwszy element poza prefiksem prawidłowego pola danych wejściowych pieniężnych. W obu przypadkach, jeśli zwracana `last`wartość jest `ios_base::eofbit` `State`równa, funkcja ustawia się w .

Druga funkcja wirtualnego chronionego elementu członkowskiego zachowuje się tak samo jak pierwsza, z tą różnicą, że w przypadku powodzenia konwertuje opcjonalnie podpisaną sekwencję cyfr na wartość typu **long double** i przechowuje tę wartość w *val*.

Format pola danych wejściowych pieniężnych jest określany przez fac aspekt ustawień**regionalnych** zwrócony przez skuteczne [wywołanie](../standard-library/locale-class.md#facet_class) [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **intl**>>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

Są to:

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) określa kolejność występowania składników pola.

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) określa kolejność elementów, która stanowi symbol waluty.

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) określa kolejność elementów, które stanowią znak dodatni.

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) określa kolejność elementów, która stanowi znak ujemny.

- **fac**. [grupowanie](../standard-library/moneypunct-class.md#grouping) określa sposób grupowania cyfr po lewej stronie dowolnego przecinka dziesiętnego.

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) określa element, który oddziela grupy cyfr po lewej stronie dowolnego przecinka dziesiętnego.

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) określa element oddzielacydycyny całkowite od cyfr ułamkowych.

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) określa liczbę cyfr ułamków znaczących po prawej stronie dowolnego przecinka dziesiętnego. Podczas analizowania kwoty pieniężnej z większą ilością cyfr `frac_digits` `do_get` ułamkowych niż jest to `frac_digits` wymagane przez , zatrzymuje analizowanie po zużyciu większości znaków.

Jeśli ciąg znaku ( **fac**. `negative_sign`lub **fac**. `positive_sign`) ma więcej niż jeden element, tylko pierwszy element jest dopasowywany, gdy element równy **money_base::sign** pojawia się we wzorcu formatu ( **fac**. `neg_format`). Wszystkie pozostałe elementy są dopasowywały na końcu pola danych wejściowych pieniężnych. Jeśli żaden z ciągów nie ma pierwszego elementu, który pasuje do następnego elementu w polu danych wejściowych pieniężnych, ciąg znaku jest traktowany jako pusty, a znak jest dodatni.

Jeśli **iosbase**. [flagi](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) jest nonzero, ciąg **fac**. `curr_symbol`musi być zgodny, gdy element **równy money_base::symbol** pojawia się we wzorcu formatu. W przeciwnym razie, jeśli **money_base::symbol** występuje na końcu wzorca formatu, a jeśli żadne elementy ciągu znaku pozostają do dopasowania, symbol waluty nie jest dopasowywać. W przeciwnym razie symbol waluty jest opcjonalnie dopasowany.

Jeśli nie ma wystąpień **fac**. `thousands_sep`występują w części wartości pola wejściowego (gdzie element **równy money_base::value** pojawia się we wzorcu formatu), nie jest nakładane żadne ograniczenie grupowania. W przeciwnym razie wszelkie ograniczenia grupowania nałożone przez **fac**. **grupowanie** jest wymuszane. Należy zauważyć, że wynikowa sekwencja cyfr reprezentuje liczbę całkowitą, której **fac**niskiego rzędu . `frac_digits`cyfry dziesiętne są traktowane po prawej stronie przecinka dziesiętnego.

Dowolna biały znak jest dopasowywać się tam, gdzie element równy **money_base::spacja** pojawia się we wzorcu formatu, jeśli pojawia się inny niż na końcu wzorca formatu. W przeciwnym razie nie jest dopasowywała wewnętrznej białej przestrzeni. Element *ch* jest uważany za biały [znak,](../standard-library/locale-functions.md#use_facet) < jeśli use_facet[ctype](../standard-library/ctype-class.md) \< **CharType**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). [jest](../standard-library/ctype-class.md#is)( **ctype_base::space**, *ch*) jest **prawdą**.

### <a name="example"></a>Przykład

Zobacz [przykład, aby](#get)uzyskać `do_get`, który wywołuje .

## <a name="money_getget"></a><a name="get"></a>money_get::get

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

*Pierwszym*\
Iterator wejściowy adresowania początku sekwencji do konwersji.

*Ostatnio*\
Iterator wprowadzania adresowania koniec sekwencji do konwersji.

*Intl*\
Wartość logiczna wskazująca typ symbolu waluty oczekiwany w sekwencji: **true** if international, **false** if domestic.

*Baza Iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny; w przeciwnym razie wymagane jest

*Państwa*\
Ustawia odpowiednie elementy maski bitowej dla stanu strumienia w zależności od tego, czy operacje zakończyły się pomyślnie.

*Val*\
Ciąg przechowujący przekonwertowane sekwencji.

### <a name="return-value"></a>Wartość zwracana

Iterator wejściowy adresowania pierwszego elementu poza pole wejściowe pieniężne.

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

## <a name="money_getiter_type"></a><a name="iter_type"></a>money_get::iter_type

Typ, który opisuje iterator danych wejściowych.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru **szablonu InputIterator**.

## <a name="money_getmoney_get"></a><a name="money_get"></a>money_get::money_get

Konstruktor obiektów typu, `money_get` które są używane do wyodrębniania wartości liczbowych z sekwencji reprezentujących wartości pieniężne.

```cpp
explicit money_get(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_refs*\
Wartość całkowita używana do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie to:

- 0: Okres istnienia obiektu jest zarządzany przez ustawienia regionalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: Te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój obiekt bazowy za pomocą **ustawień regionalnych::**[aspekt](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="money_getstring_type"></a><a name="string_type"></a>money_get::string_type

Typ opisujący ciąg zawierający znaki typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md).

## <a name="see-also"></a>Zobacz też

[\<>ustawień regionalnych](../standard-library/locale.md)\
[klasa facet](../standard-library/locale-class.md#facet_class)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

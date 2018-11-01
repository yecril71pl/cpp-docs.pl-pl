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
ms.openlocfilehash: 40ce364d768e682c9e85506d2af9e46a01c76e65
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537790"
---
# <a name="moneyget-class"></a>money_get — Klasa

Klasa szablonu opisuje obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu `CharType` na wartości pieniężne.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

*InputIterator*<br/>
Typ iteratora, z której funkcje get odczytują swoje dane wejściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba dostępu do jego przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikator.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[money_get](#money_get)|Konstruktor dla obiektów typu `money_get` służących do wyodrębniania wartości liczbowych z sekwencji reprezentujących wartości pieniężne.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wejściowych.|
|[string_type](#string_type)|Typ, który opisuje ciąg zawierający znaki typu `CharType`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[do_get](#do_get)|Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej z sekwencji znaków, która reprezentuje wartość pieniężną.|
|[get](#get)|Wyodrębnia wartość liczbową z sekwencji znaków, która reprezentuje wartość pieniężną.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="char_type"></a>  money_get::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *CharType*.

## <a name="do_get"></a>  money_get::do_get

Funkcja wirtualna wywoływana w celu wyodrębnia wartość liczbową z sekwencji znaków, która reprezentuje wartość pieniężną.

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

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się na początku sekwencji, który ma zostać przekonwertowany.

*ostatni*<br/>
Iterator danych wejściowych, odnoszący się koniec sekwencji, który ma zostać przekonwertowany.

*Wewnętrzna*<br/>
Wartość logiczną wskazującą typ symbolu waluty, oczekiwano w sekwencji: **true** Jeśli międzynarodowe, **false** Jeśli krajowych.

*iosbase*<br/>
Flagi formatu, który po zestaw wskazuje, że symbol waluty jest opcjonalna. w przeciwnym razie jest ona wymagana.

*State*<br/>
Ustawia elementy odpowiedniej maski bitów dla stanu strumień zgodnie z tego, czy operacje zakończyło się pomyślnie, czy nie.

*Val*<br/>
Ciąg przechowywania przekonwertowany sekwencji.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych, odnoszący się do pierwszego elementu poza pola pieniężnych danych wejściowych.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja wirtualna elementu członkowskiego chronionego próbuje dopasować kolejne elementy od początku sekwencji [ `first`, `last`), dopóki nie został rozpoznany kompletna, niepustych pieniężnych danych wejściowych pola. Jeśli operacja się powiedzie, konwertuje tego pola do sekwencji jednego lub więcej cyfr dziesiętnych, opcjonalnie poprzedzona znakiem minus ( `-`), aby oznaczyć i zapisuje wynik w [string_type](#string_type) obiektu *val*. Zwraca iterator, wyznaczanie pierwszego elementu poza pola pieniężnych danych wejściowych. W przeciwnym razie funkcja przechowuje pustą sekwencją w *val* i ustawia `ios_base::failbit` w *stanu*. Zwraca iterator, wyznaczanie pierwszego elementu poza dowolnego prefiksu, prawidłowego pola pieniężnych danych wejściowych. W obu przypadkach, jeśli wartość zwracana równa `last`, zestawy funkcji `ios_base::eofbit` w `State`.

Druga funkcja wirtualna elementu członkowskiego chronionego działa tak samo jak pierwszy, z tą różnicą, że w przypadku powodzenia sekwencji opcjonalnie podpisanej cyfry są konwertowane na wartość typu **typu long double** i zapisuje wynikową wartość w *val*.

Format pola pieniężnych danych wejściowych jest określany przez [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class)**fac** zwracany przez wywołanie skuteczne [use_facet](../standard-library/locale-functions.md#use_facet)  <  [ moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **intl**>> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

W szczególności:

- **FAC**. [neg_format —](../standard-library/moneypunct-class.md#neg_format) określa kolejność, w którym występują części pola.

- **FAC**. [curr_symbol —](../standard-library/moneypunct-class.md#curr_symbol) określa kolejność elementów, stanowiący symbol waluty.

- **FAC**. [positive_sign —](../standard-library/moneypunct-class.md#positive_sign) Określa sekwencję elementów, który stanowi znak wartości dodatnich.

- **FAC**. [negative_sign —](../standard-library/moneypunct-class.md#negative_sign) Określa sekwencję elementów, który stanowi znaku ujemnego.

- **FAC**. [Grupowanie](../standard-library/moneypunct-class.md#grouping) określa sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.

- **FAC**. [thousands_sep —](../standard-library/moneypunct-class.md#thousands_sep) określa element, który oddziela grup cyfr na lewo od każdego znaku dziesiętnego.

- **FAC**. [decimal_point —](../standard-library/moneypunct-class.md#decimal_point) określa element, który oddziela liczby całkowite od cyfr końcowej.

- **FAC**. [frac_digits —](../standard-library/moneypunct-class.md#frac_digits) określa liczbę cyfr znaczących ułamek z prawej strony każdego separatora dziesiętnego. Podczas analizowania kwotę pieniężną więcej cyfr ułamek nie są wymagane przez `frac_digits`, `do_get` zatrzymuje się podczas analizowania po zużyciu co najwyżej `frac_digits` znaków.

Jeśli parametry logowania ( **fac**. `negative_sign` lub **fac**. `positive_sign`) ma więcej niż jeden element, tylko pierwszy element jest dopasowywany gdy element równy **money_base::sign** pojawia się we wzorcu formatu ( **fac**. `neg_format`). Wszystkie pozostałe elementy są dopasowywane na końcu pola pieniężnych danych wejściowych. Jeśli żadna ciągu pierwszego elementu, który pasuje do następnego elementu w polu wejściowym pieniężnych, parametry logowania, wykonywana jest jako pusta, a znak jest dodatni.

Jeśli **iosbase**. [flagi](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) jest różna od zera, ciąg **fac**. `curr_symbol` musi odpowiadać gdzie element równy **money_base::symbol** pojawia się we wzorcu formatu. W przeciwnym razie, jeśli **money_base::symbol** występuje na końcu wzoru formatu i jeśli pozostają żadnych elementów ciąg znaku można dopasować, symbol waluty, nie został dopasowany. W przeciwnym razie opcjonalnie jest takie samo symbol waluty.

Jeśli nie wystąpienia **fac**. `thousands_sep` występują w część wartości pola pieniężnych danych wejściowych (gdzie element równy **money_base::value** pojawia się w wzorzec format), zostaje nałożone nie ograniczenia grupowania. W przeciwnym razie wszelkie ograniczenia grupowania nałożonych przez **fac**. **Grupowanie** jest wymuszany. Należy pamiętać, że wynikowa sekwencja cyfr reprezentuje liczbę całkowitą którego niskiego rzędu **fac**. `frac_digits` cyfry są traktowane jako po prawej stronie przecinka dziesiętnego.

Dowolny biały znak jest dopasowywany gdy element równy **money_base::space** pojawia się we wzorcu formatu, jeśli wygląda na to, innym niż na końcu wzoru formatu. W przeciwnym razie wewnętrznego biały znak nie jest dopasowany. Element *ch* jest uznawana za biały znak, jeśli [use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md) \< **CharType**>> () **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). [jest](../standard-library/ctype-class.md#is)( **ctype_base::space**, *ch*) jest **true**.

### <a name="example"></a>Przykład

Zobacz przykład [uzyskać](#get), która wywołuje metodę `do_get`.

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

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się na początku sekwencji, który ma zostać przekonwertowany.

*ostatni*<br/>
Iterator danych wejściowych, odnoszący się koniec sekwencji, który ma zostać przekonwertowany.

*Wewnętrzna*<br/>
Wartość logiczną wskazującą typ symbolu waluty, oczekiwano w sekwencji: **true** Jeśli międzynarodowe, **false** Jeśli krajowych.

*iosbase*<br/>
Flagi formatu, który po zestaw wskazuje, że symbol waluty jest opcjonalna. w przeciwnym razie jest wymagana

*State*<br/>
Ustawia elementy odpowiedniej maski bitów dla stanu strumień zgodnie z tego, czy operacje zakończyło się pomyślnie.

*Val*<br/>
Ciąg przechowywania przekonwertowany sekwencji.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych, odnoszący się do pierwszego elementu poza pola pieniężnych danych wejściowych.

### <a name="remarks"></a>Uwagi

Obie funkcje Członkowskie zwracają [do_get —](#do_get)`(first, last, Intl, Iosbase, State, val)`.

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

Typ jest synonimem dla parametru szablonu **InputIterator**.

## <a name="money_get"></a>  money_get::money_get

Konstruktor dla obiektów typu `money_get` służących do wyodrębniania wartości liczbowych z sekwencji reprezentujących wartości pieniężne.

```cpp
explicit money_get(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*<br/>
Wartość liczby całkowitej, można określić typ zarządzania pamięci dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* parametrów i ich znaczenie są:

- 0: okres istnienia obiektu jest zarządzany przez ustawienia regionalne, zawierających go.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: nie zdefiniowano tych wartości.

Żadnych przykładów bezpośrednie są to tylko możliwe, ponieważ destruktor jest chroniony.

Konstruktor inicjuje jego podstawowego obiektu z **locale::**[aspekt](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="string_type"></a>  money_get::STRING_TYPE

Typ, który opisuje ciąg zawierający znaki typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizacji szablonu klasy [basic_string](../standard-library/basic-string-class.md).

## <a name="see-also"></a>Zobacz także

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[facet — klasa](../standard-library/locale-class.md#facet_class)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

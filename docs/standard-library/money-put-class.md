---
title: money_put — Klasa
ms.date: 11/01/2018
f1_keywords:
- xlocmon/std::money_put
- xlocmon/std::money_put::char_type
- xlocmon/std::money_put::iter_type
- xlocmon/std::money_put::string_type
- xlocmon/std::money_put::do_put
- xlocmon/std::money_put::put
helpviewer_keywords:
- std::money_put [C++]
- std::money_put [C++], char_type
- std::money_put [C++], iter_type
- std::money_put [C++], string_type
- std::money_put [C++], do_put
- std::money_put [C++], put
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
ms.openlocfilehash: 035cc4e7b9cfac262979509bf7b4570e2c55336c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377430"
---
# <a name="money_put-class"></a>money_put — Klasa

Szablon klasy opisuje obiekt, który może służyć jako aspekt ustawień regionalnych do `CharType`kontrolowania konwersji wartości pieniężnych do sekwencji typu .

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class money_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

*Dane wyjścioweIterator*\
Typ iteratora, do którego funkcje pieniężne put zapisują swoje dane wyjściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[money_put](#money_put)|Konstruktor obiektów typu `money_put`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wyjściowych.|
|[string_type](#string_type)|Typ opisujący ciąg zawierający znaki `CharType`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[do_put](#do_put)|Funkcja wirtualna wywoływana w celu przekonwertowania liczby lub ciągu na sekwencję znaków, która reprezentuje wartość pieniężną.|
|[Umieścić](#put)|Konwertuje liczbę lub ciąg na sekwencję znaków, która reprezentuje wartość pieniężną.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="money_putchar_type"></a><a name="char_type"></a>money_put::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

## <a name="money_putdo_put"></a><a name="do_put"></a>money_put::do_put

Funkcja wirtualna wywoływana w celu przekonwertowania liczby lub ciągu na sekwencję znaków, która reprezentuje wartość pieniężną.

```cpp
virtual iter_type do_put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    const string_type& val) const;

virtual iter_type do_put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

### <a name="parameters"></a>Parametry

*Następnego*\
Iterator adresowania pierwszy element wstawionego ciągu.

*_Intl*\
Wartość logiczna wskazująca typ symbolu waluty oczekiwany w sekwencji: **true** if international, **false** if domestic.

*_Iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny; w przeciwnym razie wymagane jest

*_Fill*\
Znak, który jest używany do odstępów.

*Val*\
Obiekt ciągu do konwersji.

### <a name="return-value"></a>Wartość zwracana

Iterator wyjściowy adresuje pozycję jedną poza ostatnim produkowanym elementem.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja wirtualnego chronionego elementu członkowskiego generuje kolejne elementy rozpoczynające się *obok,* aby utworzyć pole wyjściowe pieniężne z [string_type](#string_type) *val*obiektu . Sekwencja kontrolowana przez *val* musi zaczynać się od jednej lub więcej cyfr dziesiętnych, opcjonalnie poprzedzonych znakiem minus (-), który reprezentuje kwotę. Funkcja zwraca iterator wyznaczający pierwszy element poza wygenerowanym polem wyjściowym pieniężnym.

Druga funkcja chronionego wirtualnego elementu członkowskiego zachowuje się tak samo jak pierwsza, z tą różnicą, że skutecznie najpierw konwertuje *val* na sekwencję cyfr dziesiętnych, opcjonalnie poprzedzone znakiem minus, a następnie konwertuje tę sekwencję jak powyżej.

Format pola wyjścia pieniężnego jest określany przez fac [aspekt ustawień regionalnych zwrócony](../standard-library/locale-class.md#facet_class) przez (skuteczne) wywołanie [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **intl**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

Są to:

- **fac**. [pos_format](../standard-library/moneypunct-class.md#pos_format) określa kolejność generowania składników pola dla wartości nieujemnej.

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) określa kolejność generowania składników pola dla wartości ujemnej.

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) określa kolejność elementów do wygenerowania dla symbolu waluty.

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) określa sekwencję elementów do wygenerowania dla znaku dodatniego.

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) określa sekwencję elementów do wygenerowania dla znaku ujemnego.

- **fac**. [grupowanie](../standard-library/moneypunct-class.md#grouping) określa sposób grupowania cyfr po lewej stronie dowolnego przecinka dziesiętnego.

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) określa element, który oddziela grupy cyfr po lewej stronie dowolnego przecinka dziesiętnego.

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) określa element, który oddziela cyfry całkowite od cyfr ułamkowych.

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) określa liczbę cyfr ułamków znaczących po prawej stronie dowolnego przecinka dziesiętnego.

Jeśli ciąg znaku ( **fac**. `negative_sign`lub **fac**. `positive_sign`) ma więcej niż jeden element, tylko pierwszy element jest generowany, gdy element **równy money_base::sign** pojawia się we wzorcu formatu ( **fac**. `neg_format`lub **fac**. `pos_format`). Wszystkie pozostałe elementy są generowane na końcu pola danych wyjściowych pieniężnych.

Jeśli **iosbase**. [flagi](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) jest nonzero, ciąg **fac**. `curr_symbol`jest generowany, gdy element równy **money_base::symbol** pojawia się we wzorcu formatu. W przeciwnym razie nie jest generowany żaden symbol waluty.

Jeśli **fac**nie narzuca żadnych ograniczeń grupowania. **grouping** (jego pierwszy element ma wartość CHAR_MAX), a następnie nie ma wystąpień **fac**. `thousands_sep`są generowane w części wartości pola wyjściowego (gdzie element **równy money_base::value** pojawia się we wzorcu formatu). Jeśli **fac**. `frac_digits`wynosi zero, to nie ma wystąpienia **fac**. `decimal_point`jest generowany po cyfrach dziesiętnych. W przeciwnym razie wynikowe pole wyjścia pieniężnego umieszcza **fac**niskiego rzędu . `frac_digits`cyfr dziesiętnych po prawej stronie przecinka dziesiętnego.

Dopełnienie występuje jak w przypadku dowolnego pola danych wyjściowych numerycznych, z tą różnicą, że jeśli **iosbase**. **flagi** & **iosbase**. [wewnętrzny](../standard-library/ios-functions.md#internal) jest niezerowy, wszystkie wewnętrzne dopełnienie jest generowany, gdzie element **równy money_base::space** pojawia się we wzorcu formatu, jeśli się pojawi. W przeciwnym razie wewnętrzne dopełnienie występuje przed wygenerowaną sekwencją. Znak dopełnienia jest **wypełnienie**.

Funkcja wywołuje **iosbase**. **szerokości**(0), aby zresetować szerokość pola do zera.

### <a name="example"></a>Przykład

Zobacz przykład [put](#put), gdzie funkcja wirtualnego elementu członkowskiego jest wywoływana przez **put**.

## <a name="money_putiter_type"></a><a name="iter_type"></a>money_put::iter_type

Typ, który opisuje iterator danych wyjściowych.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **OutputIterator.**

## <a name="money_putmoney_put"></a><a name="money_put"></a>money_put::money_put

Konstruktor obiektów typu `money_put`.

```cpp
explicit money_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_refs*\
Wartość całkowita używana do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie to:

- 0: okres istnienia obiektu jest zarządzany przez ustawienia regionalne, które go zawierają.

- 1: okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój obiekt bazowy `_Refs`za pomocą **ustawień regionalnych::**[aspekt](../standard-library/locale-class.md#facet_class)( ).

## <a name="money_putput"></a><a name="put"></a>money_put::put

Konwertuje liczbę lub ciąg na sekwencję znaków, która reprezentuje wartość pieniężną.

```cpp
iter_type put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    const string_type& val) const;

iter_type put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

### <a name="parameters"></a>Parametry

*Następnego*\
Iterator adresowania pierwszy element wstawionego ciągu.

*_Intl*\
Wartość logiczna wskazująca typ symbolu waluty oczekiwany w sekwencji: **true** if international, **false** if domestic.

*_Iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny; w przeciwnym razie wymagane jest

*_Fill*\
Znak, który jest używany do odstępów.

*Val*\
Obiekt ciągu do konwersji.

### <a name="return-value"></a>Wartość zwracana

Iterator wyjściowy adresuje pozycję jedną poza ostatnim produkowanym elementem.

### <a name="remarks"></a>Uwagi

Obie funkcje [do_put](#do_put)członkowskie zwracają `next`do_put `_Intl` `_Iosbase`( `_Fill` `val`, , , , ).

### <a name="example"></a>Przykład

```cpp
// money_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

int main()
{
    std::locale loc( "german_germany" );
    std::basic_stringstream<char> psz;

    psz.imbue(loc);
    psz.flags(psz.flags() | std::ios_base::showbase); // force the printing of the currency symbol
    std::use_facet<std::money_put<char> >(loc).put(std::basic_ostream<char>::_Iter(psz.rdbuf()), true, psz, ' ', 100012);
    if (psz.fail())
        std::cout << "money_put() FAILED" << std::endl;
    else
        std::cout << "money_put() = \"" << psz.rdbuf()->str() << "\"" << std::endl;
}
```

```Output
money_put() = "EUR1.000,12"
```

## <a name="money_putstring_type"></a><a name="string_type"></a>money_put::string_type

Typ opisujący ciąg zawierający znaki `CharType`typu .

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) którego obiekty mogą przechowywać sekwencje elementów z sekwencji źródłowej.

## <a name="see-also"></a>Zobacz też

[\<>ustawień regionalnych](../standard-library/locale.md)\
[klasa facet](../standard-library/locale-class.md#facet_class)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

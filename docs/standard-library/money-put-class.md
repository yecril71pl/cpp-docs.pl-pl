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
ms.openlocfilehash: d15667f4e30561dbba024f877530c4ff0f824f64
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224750"
---
# <a name="money_put-class"></a>money_put — Klasa

Szablon klasy opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontroli konwersji wartości pieniężnych na sekwencje typu `CharType` .

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class money_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

*OutputIterator*\
Typ iteratora, do którego funkcje pieniężne put zapisują swoje dane wyjściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[money_put](#money_put)|Konstruktor dla obiektów typu `money_put` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wyjściowych.|
|[string_type](#string_type)|Typ, który opisuje ciąg zawierający znaki typu `CharType` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[do_put](#do_put)|Funkcja wirtualna wywoływana w celu przekonwertowania liczby lub ciągu na sekwencję znaków, która reprezentuje wartość pieniężną.|
|[Ubrani](#put)|Konwertuje liczbę lub ciąg na sekwencję znaków, która reprezentuje wartość pieniężną.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<locale>

**Przestrzeń nazw:** std

## <a name="money_putchar_type"></a><a name="char_type"></a>money_put:: char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **CharType**.

## <a name="money_putdo_put"></a><a name="do_put"></a>money_put::d o_put

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

*ponown*\
Iterator odnoszący się do pierwszego elementu wstawionego ciągu.

*_Intl*\
Wartość logiczna wskazująca typ symbolu waluty oczekiwanego w sekwencji: **`true`** Jeśli międzynarodowy, jeśli jest to **`false`** obcy.

*_Iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny. w przeciwnym razie jest to wymagane

*_Fill*\
Znak, który jest używany na potrzeby odstępów.

*użyte*\
Obiekt ciągu do przekonwertowania.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnosi się do położenia jednej poza ostatnim produkowanym elementem.

### <a name="remarks"></a>Uwagi

Pierwsza wirtualna chroniona funkcja składa generuje sekwencyjne elementy, zaczynając od *następnego* , aby utworzyć pole danych wyjściowych pieniężnych z obiektu [string_type](#string_type) *Val*. Sekwencja kontrolowana przy użyciu wartości *Val* musi rozpoczynać się od co najmniej jednej cyfry dziesiętnej, opcjonalnie poprzedzonej znakiem minus (-), która reprezentuje wartość. Funkcja zwraca iterator wyznaczający pierwszy element wykraczający poza wygenerowane pole danych wyjściowych pieniężnych.

Druga wirtualna funkcja chroniona jest taka sama jak pierwsza, z tą różnicą, że najpierw konwertuje wartość *Val* na sekwencję cyfr dziesiętnych, opcjonalnie poprzedzoną znakiem minus, a następnie konwertuje tę sekwencję jak powyżej.

Format pola danych wyjściowych pieniężnych jest określany przez zestaw [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class) FAC zwrócony przez (efektywne) wywołania [use_facet](../standard-library/locale-functions.md#use_facet)  <  [moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **intl**> > ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

W szczególności:

- **FAC**. [pos_format](../standard-library/moneypunct-class.md#pos_format) określa kolejność, w jakiej składniki pola są generowane dla nieujemnej wartości.

- **FAC**. [neg_format](../standard-library/moneypunct-class.md#neg_format) określa kolejność, w jakiej składniki pola są generowane dla wartości ujemnej.

- **FAC**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) Określa sekwencję elementów do wygenerowania dla symbolu waluty.

- **FAC**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) Określa sekwencję elementów do wygenerowania dla znaku dodatniego.

- **FAC**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) Określa sekwencję elementów do wygenerowania dla znaku minus.

- **FAC**. [grupowanie](../standard-library/moneypunct-class.md#grouping) określa sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego.

- **FAC**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) określa element oddzielający grupy cyfr po lewej stronie dowolnego miejsca dziesiętnego.

- **FAC**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) określa element oddzielający cyfry całkowite od dowolnych cyfr ułamkowych.

- **FAC**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) określa liczbę znaczących cyfr ułamków po prawej stronie dowolnego punktu dziesiętnego.

Jeśli ciąg znaków ( **FAC**. `negative_sign`lub **FAC**. `positive_sign`) ma więcej niż jeden element, jest generowany tylko pierwszy element, gdzie element jest równy **money_base:: Sign** jest wyświetlany w wzorcu formatu ( **FAC**. `neg_format`lub **FAC**. `pos_format`). Wszystkie pozostałe elementy są generowane na końcu pola danych wyjściowych pieniężnych.

Jeśli **iosbase**. [flagi](../standard-library/ios-base-class.md#flags)  &  [showbase](../standard-library/ios-functions.md#showbase) jest różna od zera, ciąg **FAC**. `curr_symbol`jest generowana, gdy element jest równy **money_base:: symbol** jest wyświetlany w wzorcu formatu. W przeciwnym razie nie zostanie wygenerowany żaden symbol waluty.

Jeśli żadne ograniczenia grupowania nie są nakładane przez **FAC**. **grupowanie** (jego pierwszy element ma wartość CHAR_MAX), a następnie brak wystąpień elementu **FAC**. `thousands_sep`są generowane w części wartości pola danych wyjściowych pieniężnych (gdzie element jest równy **money_base:: value** pojawia się we wzorcu formatu). Jeśli **FAC**. `frac_digits`to zero, a nie wystąpienie elementu **FAC**. `decimal_point`jest generowany po cyfrach dziesiętnych. W przeciwnym razie wynikowe pole danych wyjściowych jest umieszczane w **FAC**o niskiej kolejności. `frac_digits`cyfry dziesiętne z prawej strony punktu dziesiętnego.

Uzupełnienie ma miejsce dla dowolnego pola danych wyjściowych, z wyjątkiem tego, że jeśli **iosbase**. **flagi**  &  **iosbase**. [wewnętrzna](../standard-library/ios-functions.md#internal) jest różna od zera, zostanie wygenerowane dopełnienie wewnętrzne, gdzie element jest równy **money_base:: spacja** pojawia się w wzorcu formatu, jeśli jest wyświetlany. W przeciwnym razie dopełnienie wewnętrzne występuje przed wygenerowaną sekwencją. Znak uzupełniania jest **wypełniany**.

Funkcja wywołuje **iosbase**. **Szerokość**(0), aby zresetować szerokość pola do zera.

### <a name="example"></a>Przykład

Zobacz przykład dla funkcji [Put](#put), gdzie wirtualna funkcja członkowska jest wywoływana przez funkcję **Put**.

## <a name="money_putiter_type"></a><a name="iter_type"></a>money_put:: iter_type

Typ, który opisuje iterator danych wyjściowych.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **OutputIterator.**

## <a name="money_putmoney_put"></a><a name="money_put"></a>money_put:: money_put

Konstruktor dla obiektów typu `money_put` .

```cpp
explicit money_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Wartość całkowita służąca do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie są następujące:

- 0: okres istnienia obiektu jest zarządzany przez elementy lokalne, które go zawierają.

- 1: okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój obiekt podstawowy przy użyciu **ustawień regionalnych::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs` ).

## <a name="money_putput"></a><a name="put"></a>money_put::p UT

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

*ponown*\
Iterator odnoszący się do pierwszego elementu wstawionego ciągu.

*_Intl*\
Wartość logiczna wskazująca typ symbolu waluty oczekiwanego w sekwencji: **`true`** Jeśli międzynarodowy, jeśli jest to **`false`** obcy.

*_Iosbase*\
Flaga formatu, która po ustawieniu wskazuje, że symbol waluty jest opcjonalny. w przeciwnym razie jest to wymagane

*_Fill*\
Znak, który jest używany na potrzeby odstępów.

*użyte*\
Obiekt ciągu do przekonwertowania.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnosi się do położenia jednej poza ostatnim produkowanym elementem.

### <a name="remarks"></a>Uwagi

Obie funkcje członkowskie zwracają [do_put](#do_put)( `next` , `_Intl` ,,, `_Iosbase` `_Fill` `val` ).

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

## <a name="money_putstring_type"></a><a name="string_type"></a>money_put:: string_type

Typ, który opisuje ciąg zawierający znaki typu `CharType` .

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) którego obiekty mogą przechowywać sekwencje elementów z sekwencji źródłowej.

## <a name="see-also"></a>Zobacz także

[\<locale>](../standard-library/locale.md)\
[facet — Klasa](../standard-library/locale-class.md#facet_class)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

---
title: regex_iterator — Klasa
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_iterator
- regex/std::regex_iterator::operator==
- regex/std::regex_iterator::operator!=
- regex/std::regex_iterator::operator*
- regex/std::regex_iterator::operator->
- regex/std::regex_iterator::operator++
helpviewer_keywords:
- std::regex_iterator
- std::regex_iterator::operator==
- std::regex_iterator::operator!=
- std::regex_iterator::operator*
- std::regex_iterator::operator->
- std::regex_iterator::operator++
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
ms.openlocfilehash: ccf806a7918100c58e04ab403f3a8b895e8dc256
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451558"
---
# <a name="regexiterator-class"></a>regex_iterator — Klasa

Klasa iteratora dla dopasowania.

## <a name="syntax"></a>Składnia

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>Parametry

*BidIt*\
Typ iteratora dla podpasowań.

*Elem*\
Typ elementów, do których ma pasować.

*RXtraits*\
Klasa cech dla elementów.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje stały obiekt iteratora do przodu. Wyodrębnia obiekty typu `match_results<BidIt>` przez wielokrotnie stosując swój obiekt `*pregex` wyrażenia regularnego do sekwencji znaków zdefiniowanej przez zakres `[begin, end)`iteratora.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[regex_iterator](#regex_iterator)|Konstruuje iterator.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[difference_type](#difference_type)|Typ różnicy iteratora.|
|[iterator_category](#iterator_category)|Typ kategorii iteratora.|
|[pointer](#pointer)|Typ wskaźnika do dopasowania.|
|[Odwołanie](#reference)|Typ odwołania do dopasowania.|
|[regex_type](#regex_type)|Typ wyrażenia regularnego do dopasowania.|
|[value_type](#value_type)|Typ dopasowania.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Porównuje Iteratory pod kątem nierówności.|
|[zakład](#op_star)|Uzyskuje dostęp do wyszukanego dopasowania.|
|[operator++](#op_add_add)|Zwiększa iterator.|
|[operator=](#op_eq)|Porównuje Iteratory dla równości.|
|[operator — >](#op_arrow)|Uzyskuje dostęp do wyszukanego dopasowania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> wyrażeń regularnych

**Przestrzeń nazw:** std

## <a name="examples"></a>Przykłady

Zobacz następujące tematy dotyczące przykładów w wyrażeniach regularnych:

- [regex_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [swap](../standard-library/regex-functions.md#swap)

```cpp
// std__regex__regex_iterator.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "axayaz";
    Myiter::regex_type rx("a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;

// other members
    Myiter it1(pat, pat + strlen(pat), rx);
    Myiter it2(it1);
    next = it1;

    Myiter::iterator_category cat = std::forward_iterator_tag();
    Myiter::difference_type dif = -3;
    Myiter::value_type mr = *it1;
    Myiter::reference ref = mr;
    Myiter::pointer ptr = &ref;

    dif = dif; // to quiet "unused" warnings
    ptr = ptr;

    return (0);
    }
```

```Output
match == a
match == a
match == a
```

## <a name="difference_type"></a>regex_iterator::d ifference_type

Typ różnicy iteratora.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `std::ptrdiff_t`.

## <a name="iterator_category"></a>regex_iterator::iterator_category

Typ kategorii iteratora.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `std::forward_iterator_tag`.

## <a name="op_neq"></a>regex_iterator:: operator! =

Porównuje Iteratory pod kątem nierówności.

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Iterator, do którego ma zostać wykonane porównanie.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `!(*this == right)`wartość.

## <a name="op_star"></a>regex_iterator:: operator *

Uzyskuje dostęp do wyszukanego dopasowania.

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywaną wartość `match`.

## <a name="op_add_add"></a>regex_iterator:: operator + +

Zwiększa iterator.

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>Uwagi

Jeśli bieżące dopasowanie nie ma znaków od pierwszego wywołania `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`operatora; w przeciwnym razie zwiększa wartość `begin` przechowywaną, aby wskazywała na pierwszy znak po bieżącym dopasowaniu, a `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`następnie wywołuje. W obu przypadkach, jeśli wyszukiwanie nie powiedzie się, operator ustawia element na End-of-Sequence iteratora. Operator zwraca obiekt.

Drugi operator wykonuje kopię obiektu, zwiększa obiekt, a następnie zwraca kopię.

## <a name="op_eq"></a>regex_iterator:: operator =

Porównuje Iteratory dla równości.

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Iterator, do którego ma zostać wykonane porównanie.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość PRAWDA `*this` , jeśli i *prawe* są iteratorami końca sekwencji lub jeśli żaden z nich nie jest `begin == right.begin` `pregex == right.pregex`iteratorem końcowym sekwencji i, `end == right.end`,, i `flags == right.flags`. W przeciwnym razie zwraca wartość false.

## <a name="op_arrow"></a>regex_iterator:: operator-&gt;

Uzyskuje dostęp do wyszukanego dopasowania.

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca adres przechowywanej wartości `match`.

## <a name="pointer"></a>regex_iterator::p ointer

Typ wskaźnika do dopasowania.

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `match_results<BidIt>*`, gdzie `BidIt` jest parametrem szablonu.

## <a name="reference"></a>regex_iterator:: Reference

Typ odwołania do dopasowania.

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `match_results<BidIt>&`, gdzie `BidIt` jest parametrem szablonu.

## <a name="regex_iterator"></a>regex_iterator::regex_iterator

Konstruuje iterator.

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Początek sekwencji do dopasowania.

*ostatniego*\
Koniec sekwencji do dopasowania.

*Eksport*\
Wyrażenie regularne dla dopasowania.

*n*\
Flagi dla dopasowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje iterator końca sekwencji. Drugi Konstruktor inicjuje przechowywaną wartość `begin` przy *pierwszej*, przechowywaną wartość `end` z *ostatnią*, przechowywaną `pregex` wartością z `&re`i przechowywaną wartością `flags` w *f*. Następnie wywołuje `regex_search(begin, end, match, *pregex, flags)`. Jeśli wyszukiwanie nie powiedzie się, Konstruktor ustawi obiekt na iterator sekwencji końcowej.

## <a name="regex_type"></a>regex_iterator::regex_type

Typ wyrażenia regularnego do dopasowania.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Uwagi

Element typedef jest synonimem dla `basic_regex<Elem, RXtraits>`.

## <a name="value_type"></a>regex_iterator::value_type

Typ dopasowania.

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `match_results<BidIt>`, gdzie `BidIt` jest parametrem szablonu.

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)\
[Klasa regex_constants](../standard-library/regex-constants-class.md)\
[Klasa regex_error](../standard-library/regex-error-class.md)\
[\<Funkcje > wyrażenia regularnego](../standard-library/regex-functions.md)\
[Klasa regex_iterator](../standard-library/regex-iterator-class.md)\
[\<Operatory > wyrażenia regularnego](../standard-library/regex-operators.md)\
[Klasa regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Klasa regex_traits](../standard-library/regex-traits-class.md)\
[\<wyrażenie regularne > Typedefs](../standard-library/regex-typedefs.md)

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
ms.openlocfilehash: 6bc57d6815fa6f30e26b22e9b7ab758a1ac20e16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374553"
---
# <a name="regex_iterator-class"></a>regex_iterator — Klasa

Klasa iteratora dla meczów.

## <a name="syntax"></a>Składnia

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>Parametry

*OfertaIt*\
Typ iteratora dla podmeczów.

*Elem*\
Typ elementów, do których ma pasować.

*RXtraits ( RXtraits )*\
Klasa cech dla elementów.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje stały obiekt iteratora do przodu. Wyodrębnia obiekty typu, `match_results<BidIt>` wielokrotnie stosując jego obiekt `*pregex` wyrażenia regularnego do sekwencji znaków `[begin, end)`zdefiniowanej przez zakres iteratora .

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[regex_iterator](#regex_iterator)|Konstruuje iteratora.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[difference_type](#difference_type)|Typ różnicy iteratora.|
|[Iterator_category](#iterator_category)|Typ kategorii iteratora.|
|[pointer](#pointer)|Typ wskaźnika do dopasowania.|
|[Odwołanie](#reference)|Typ odwołania do dopasowania.|
|[regex_type](#regex_type)|Typ wyrażenia regularnego do dopasowania.|
|[value_type](#value_type)|Typ dopasowania.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Porównuje iteratory dla nierówności.|
|[operator*](#op_star)|Uzyskuje dostęp do wyznaczonego dopasowania.|
|[operator++](#op_add_add)|Zwiększa iteratora.|
|[operator=](#op_eq)|Porównuje iteratory dla równości.|
|[operator->](#op_arrow)|Uzyskuje dostęp do wyznaczonego dopasowania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> regex

**Przestrzeń nazw:** std

## <a name="examples"></a>Przykłady

Zobacz następujące tematy, aby zapoznać się z przykładami wyrażeń regularnych:

- [regex_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [Wymiany](../standard-library/regex-functions.md#swap)

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

## <a name="regex_iteratordifference_type"></a><a name="difference_type"></a>regex_iterator::d00_typ

Typ różnicy iteratora.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `std::ptrdiff_t`.

## <a name="regex_iteratoriterator_category"></a><a name="iterator_category"></a>regex_iterator::iterator_category

Typ kategorii iteratora.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `std::forward_iterator_tag`.

## <a name="regex_iteratoroperator"></a><a name="op_neq"></a>regex_iterator::operator!=

Porównuje iteratory dla nierówności.

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Iterator do porównania.

### <a name="remarks"></a>Uwagi

Funkcja elementu `!(*this == right)`członkowskiego zwraca .

## <a name="regex_iteratoroperator"></a><a name="op_star"></a>regex_iterator::operator*

Uzyskuje dostęp do wyznaczonego dopasowania.

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `match`wartość zapisaną .

## <a name="regex_iteratoroperator"></a><a name="op_add_add"></a>regex_iterator::operator++

Zwiększa iteratora.

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>Uwagi

Jeśli bieżące dopasowanie nie ma `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`znaków, pierwszy operator wywołuje; w przeciwnym razie `begin` przesuwa zapisaną wartość, aby wskazać `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`pierwszy znak po bieżącym dopasowaniu, a następnie wywołuje . W obu przypadkach, jeśli wyszukiwanie zakończy się niepowodzeniem, operator ustawia obiekt na iterator końca sekwencji. Operator zwraca obiekt.

Drugi operator tworzy kopię obiektu, zwiększa obiekt, a następnie zwraca kopię.

## <a name="regex_iteratoroperator"></a><a name="op_eq"></a>regex_iterator::operator=

Porównuje iteratory dla równości.

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Iterator do porównania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego `*this` zwraca wartość true, jeśli i *po prawej stronie* są zarówno iteratory końca sekwencji, jak i jeśli żadna z nich nie jest iteratorem końca sekwencji i `begin == right.begin`, `end == right.end`, `pregex == right.pregex`i `flags == right.flags`. W przeciwnym razie zwraca wartość false.

## <a name="regex_iteratoroperator-gt"></a><a name="op_arrow"></a>regex_iterator::operator-&gt;

Uzyskuje dostęp do wyznaczonego dopasowania.

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca adres `match`zapisanej wartości .

## <a name="regex_iteratorpointer"></a><a name="pointer"></a>regex_iterator::pointer

Typ wskaźnika do dopasowania.

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `match_results<BidIt>*`, `BidIt` gdzie jest parametr szablonu.

## <a name="regex_iteratorreference"></a><a name="reference"></a>regex_iterator::odwołanie

Typ odwołania do dopasowania.

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `match_results<BidIt>&`, `BidIt` gdzie jest parametr szablonu.

## <a name="regex_iteratorregex_iterator"></a><a name="regex_iterator"></a>regex_iterator::regex_iterator

Konstruuje iteratora.

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Początek sekwencji do dopasowania.

*Ostatnio*\
Koniec sekwencji do dopasowania.

*Ponownie*\
Wyrażenie regularne dla dopasowań.

*F*\
Flagi dla meczów.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor tworzy iterator końca sekwencji. Drugi konstruktor inicjuje `begin` wartość przechowywaną `end` z *pierwszą,* przechowywaną wartością `flags` z *ostatnią,* zapisaną wartością `pregex` z `&re`, i wartością przechowywaną z *f*. Następnie wywołuje `regex_search(begin, end, match, *pregex, flags)`. Jeśli wyszukiwanie zakończy się niepowodzeniem, konstruktor ustawia obiekt na iterator końca sekwencji.

## <a name="regex_iteratorregex_type"></a><a name="regex_type"></a>regex_iterator::regex_type

Typ wyrażenia regularnego do dopasowania.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem `basic_regex<Elem, RXtraits>`.

## <a name="regex_iteratorvalue_type"></a><a name="value_type"></a>regex_iterator::value_type

Typ dopasowania.

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `match_results<BidIt>`, `BidIt` gdzie jest parametr szablonu.

## <a name="see-also"></a>Zobacz też

[\<>regex](../standard-library/regex.md)\
[Klasa regex_constants](../standard-library/regex-constants-class.md)\
[Klasa regex_error](../standard-library/regex-error-class.md)\
[\<funkcje> regex](../standard-library/regex-functions.md)\
[Klasa regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operatorzy> regex](../standard-library/regex-operators.md)\
[Klasa regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Klasa regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)

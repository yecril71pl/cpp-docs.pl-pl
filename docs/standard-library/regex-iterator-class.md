---
title: regex_iterator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::regex_iterator
- regex/std::regex_iterator::operator==
- regex/std::regex_iterator::operator!=
- regex/std::regex_iterator::operator*
- regex/std::regex_iterator::operator->
- regex/std::regex_iterator::operator++
dev_langs:
- C++
helpviewer_keywords:
- std::regex_iterator
- std::regex_iterator::operator==
- std::regex_iterator::operator!=
- std::regex_iterator::operator*
- std::regex_iterator::operator->
- std::regex_iterator::operator++
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b723294c0ecdbdf585acecc257174251b13d56ca
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710362"
---
# <a name="regexiterator-class"></a>regex_iterator — Klasa

Iterator — klasa dopasowania.

## <a name="syntax"></a>Składnia

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>Parametry

*BidIt*<br/>
Typ iteratora poddopasowania.

*Elem*<br/>
Typ elementów, do których ma pasować.

*RXtraits*<br/>
Klasa cech dla elementów.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt stały iterator do przodu. Wyodrębnia obiekty typu `match_results<BidIt>` wielokrotnie, stosując jego obiektu będącego wyrażeniem regularnym `*pregex` sekwencję znaków, definiowane przez zakres iteratora `[begin, end)`.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[regex_iterator](#regex_iterator)|Tworzy iterator.|

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
|[operator *](#op_star)|Uzyskuje dostęp do wyznaczonej dopasowania.|
|[operator++](#op_add_add)|Inkrementuje iterator.|
|[operator=](#op_eq)|Porównuje Iteratory pod kątem równości.|
|[operator ->](#op_arrow)|Uzyskuje dostęp do wyznaczonej dopasowania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyrażenia regularnego >

**Namespace:** standardowe

## <a name="examples"></a>Przykłady

Zobacz poniższe tematy zawierają przykłady dotyczące wyrażeń regularnych:

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

## <a name="difference_type"></a>  regex_iterator::difference_type

Typ różnicy iteratora.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `std::ptrdiff_t`.

## <a name="iterator_category"></a>  regex_iterator::iterator_category

Typ kategorii iteratora.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `std::forward_iterator_tag`.

## <a name="op_neq"></a>  regex_iterator::operator! =

Porównuje Iteratory pod kątem nierówności.

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Iterator do porównania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `!(*this == right)`.

## <a name="op_star"></a>  regex_iterator::operator *

Uzyskuje dostęp do wyznaczonej dopasowania.

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca przechowywaną wartość `match`.

## <a name="op_add_add"></a>  regex_iterator::operator ++

Inkrementuje iterator.

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>Uwagi

Jeśli bieżące dopasowanie nie ma żadnych znaków pierwszy operator wywołuje `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`; w przeciwnym razie przechodzi przechowywaną wartość `begin` wskaż pierwszy znak po bieżącej następnie dopasowywania wywołań `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`. W obu przypadkach Jeśli wyszukiwanie zakończy się niepowodzeniem, operator ustawia obiekt iteratora sekwencja kończenia. Operator zwraca obiekt.

Drugi operator tworzy kopię obiektu, zwiększa obiektu, a następnie zwraca kopię.

## <a name="op_eq"></a>  regex_iterator::operator =

Porównuje Iteratory pod kątem równości.

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Iterator do porównania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość PRAWDA, jeśli `*this` i *prawo* Iteratory sekwencja kończenia lub jeśli żadna z nich nie jest iteratorem sekwencja kończenia i `begin == right.begin`, `end == right.end`, `pregex == right.pregex`, i `flags == right.flags`. W przeciwnym razie zwraca wartość false.

## <a name="op_arrow"></a>  regex_iterator::operator-&gt;

Uzyskuje dostęp do wyznaczonej dopasowania.

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca adres przechowywaną wartość `match`.

## <a name="pointer"></a>  regex_iterator::Pointer

Typ wskaźnika do dopasowania.

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `match_results<BidIt>*`, gdzie `BidIt` jest parametr szablonu.

## <a name="reference"></a>  regex_iterator::Reference

Typ odwołania do dopasowania.

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `match_results<BidIt>&`, gdzie `BidIt` jest parametr szablonu.

## <a name="regex_iterator"></a>  regex_iterator::regex_iterator

Tworzy iterator.

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Początek sekwencji w celu dopasowania.

*ostatni*<br/>
Koniec sekwencji w celu dopasowania.

*środowisko odzyskiwania*<br/>
Wyrażenie regularne do dopasowania.

*f*<br/>
Flagi dopasowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje iterator sekwencja kończenia. Drugi Konstruktor inicjuje przechowywaną wartość `begin` z *pierwszy*, przechowywaną wartość `end` z *ostatniego*, przechowywaną wartość `pregex` z `&re`i przechowywaną wartość `flags` z *f*. Następnie wywołuje `regex_search(begin, end, match, *pregex, flags)`. Jeśli wyszukiwanie zakończy się niepowodzeniem, Konstruktor ustawia obiekt do iteratora sekwencja kończenia.

## <a name="regex_type"></a>  regex_iterator::regex_type

Typ wyrażenia regularnego do dopasowania.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem dla `basic_regex<Elem, RXtraits>`.

## <a name="value_type"></a>  regex_iterator::value_type

Typ dopasowania.

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `match_results<BidIt>`, gdzie `BidIt` jest parametr szablonu.

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants, klasa](../standard-library/regex-constants-class.md)<br/>
[regex_error, klasa](../standard-library/regex-error-class.md)<br/>
[\<wyrażenie regularne > funkcji](../standard-library/regex-functions.md)<br/>
[regex_iterator, klasa](../standard-library/regex-iterator-class.md)<br/>
[\<wyrażenie regularne > operatorów](../standard-library/regex-operators.md)<br/>
[regex_token_iterator, klasa](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits, klasa](../standard-library/regex-traits-class.md)<br/>
[\<wyrażenie regularne > definicje typów](../standard-library/regex-typedefs.md)<br/>

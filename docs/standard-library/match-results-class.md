---
title: match_results — Klasa
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: 72a948c7f8422b36b94a16cdb2c815bca92d20c7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456387"
---
# <a name="matchresults-class"></a>match_results — Klasa

Przechowuje sekwencję podpasowań.

## <a name="syntax"></a>Składnia

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>Parametry

*BidIt*\
Typ iteratora dla podpasowań.

*Alokacj*\
Typ alokatora do zarządzania pamięcią.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który kontroluje niemodyfikowalną sekwencję elementów typu `sub_match<BidIt>` wygenerowanego przez wyszukiwanie wyrażenia regularnego. Każdy element wskazuje podsekwencję, która była zgodna z grupą przechwytywania odpowiadającą temu elementowi.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[match_results](#match_results)|Konstruuje obiekt.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ alokatora do zarządzania pamięcią.|
|[char_type](#char_type)|Typ elementu.|
|[const_iterator](#const_iterator)|Typ iteratora const dla podpasowań.|
|[const_reference](#const_reference)|Typ odwołania do elementu const.|
|[difference_type](#difference_type)|Typ różnicy iteratora.|
|[iterator](#iterator)|Typ iteratora dla podpasowań.|
|[Odwołanie](#reference)|Typ odwołania do elementu.|
|[size_type](#size_type)|Typ liczby poddopasowywania.|
|[string_type](#string_type)|Typ ciągu.|
|[value_type](#value_type)|Typ poddopasowania.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[begin](#begin)|Określa początek sekwencji poddopasowywania.|
|[empty](#empty)|Testuje brak podpasowań.|
|[punktów](#end)|Określa koniec sekwencji poddopasowywania.|
|[format](#format)|Poddopasowania formatów.|
|[get_allocator](#get_allocator)|Zwraca przechowywany program przydzielający.|
|[length](#length)|Zwraca długość poddopasowania.|
|[max_size](#max_size)|Pobiera największą liczbę podpasowań.|
|[umieścić](#position)|Pobierz początkowe przesunięcie podgrupy.|
|[prefix](#prefix)|Pobiera sekwencję przed pierwszym poddopasowaniem.|
|[zmienia](#size)|Liczy liczbę podpasowań.|
|[str](#str)|Zwraca poddopasowanie.|
|[suffix](#suffix)|Pobiera sekwencję po ostatnim dopasowań.|
|[swap](#swap)|Zamienia dwa obiekty match_results.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Skopiuj obiekt match_results.|
|[zakład\[\]](#op_at)|Dostęp do podobiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> wyrażeń regularnych

**Przestrzeń nazw:** std

## <a name="example"></a>Przykład

```cpp
// std__regex__match_results.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::cout << "prefix: matched == " << std::boolalpha
        << mr.prefix().matched
        << ", value == " << mr.prefix() << std::endl;
    std::cout << "whole match: " << mr.length() << " chars, value == "
        << mr.str() << std::endl;
    std::cout << "suffix: matched == " << std::boolalpha
        << mr.suffix().matched
        << ", value == " << mr.suffix() << std::endl;
    std::cout << std::endl;

    std::string fmt("\"c(a*)|(b)\" matched \"$&\"\n"
        "\"(a*)\" matched \"$1\"\n"
        "\"(b)\" matched \"$2\"\n");
    std::cout << mr.format(fmt) << std::endl;
    std::cout << std::endl;

    // index through submatches
    for (size_t n = 0; n < mr.size(); ++n)
    {
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha
            << mr[n].matched <<
            " at position " << mr.position(n) << std::endl;
        std::cout << "  " << mr.length(n)
            << " chars, value == " << mr[n] << std::endl;
    }
    std::cout << std::endl;

    // iterate through submatches
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)
    {
        std::cout << "next submatch: matched == " << std::boolalpha
            << it->matched << std::endl;
        std::cout << "  " << it->length()
            << " chars, value == " << *it << std::endl;
    }
    std::cout << std::endl;

    // other members
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;

    std::cmatch::allocator_type al = mr.get_allocator();
    std::cmatch::string_type str = std::string("x");
    std::cmatch::size_type maxsiz = mr.max_size();
    std::cmatch::char_type ch = 'x';
    std::cmatch::difference_type dif = mr.begin() - mr.end();
    std::cmatch::const_iterator cit = mr.begin();
    std::cmatch::value_type val = *cit;
    std::cmatch::const_reference cref = val;
    std::cmatch::reference ref = val;

    maxsiz = maxsiz;  // to quiet "unused" warnings
    if (ref == cref)
        ch = ch;
    dif = dif;

    return (0);
}
```

```Output
prefix: matched == true, value == x
whole match: 4 chars, value == caaa
suffix: matched == true, value == y

"c(a*)|(b)" matched "caaa"
"(a*)" matched "aaa"
"(b)" matched ""

submatch[0]: matched == true at position 1
  4 chars, value == caaa
submatch[1]: matched == true at position 2
  3 chars, value == aaa
submatch[2]: matched == false at position 6
  0 chars, value ==

next submatch: matched == true
  4 chars, value == caaa
next submatch: matched == true
  3 chars, value == aaa
next submatch: matched == false
  0 chars, value ==

empty == false
```

## <a name="allocator_type"></a>match_results::allocator_type

Typ alokatora do zarządzania pamięcią.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Uwagi

Element typedef jest synonimem dla *alokacji*argumentu szablonu.

## <a name="begin"></a>match_results:: BEGIN

Określa początek sekwencji poddopasowywania.

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator dostępu losowego, który wskazuje na pierwszy element sekwencji (lub tuż poza końcem pustej sekwencji).

## <a name="char_type"></a>match_results::char_type

Typ elementu.

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>Uwagi

Element typedef jest synonimem typu `iterator_traits<BidIt>::value_type`, który jest typem elementu przeszukiwanej sekwencji znaków.

## <a name="const_iterator"></a>match_results::const_iterator

Typ iteratora const dla podpasowań.

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>Uwagi

Element typedef opisuje obiekt, który może być używany jako iterator stałego dostępu swobodnego dla kontrolowanej sekwencji.

## <a name="const_reference"></a>match_results::const_reference

Typ odwołania do elementu const.

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

Element typedef opisuje obiekt, który może stanowić stałe odwołanie do elementu kontrolowanej sekwencji.

## <a name="difference_type"></a>match_results::d ifference_type

Typ różnicy iteratora.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Element typedef jest synonimem dla typu `iterator_traits<BidIt>::difference_type`; opisuje obiekt, który może reprezentować różnicę między dwoma iteratorami, które wskazują na elementy kontrolowanej sekwencji.

## <a name="empty"></a>match_results:: Empty

Testuje brak podpasowań.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość true tylko wtedy, gdy wyszukiwanie wyrażenia regularnego nie powiodło się.

## <a name="end"></a>match_results:: end

Określa koniec sekwencji poddopasowywania.

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca iterator, który wskazuje tuż poza końcem sekwencji.

## <a name="format"></a>match_results:: format

Poddopasowania formatów.

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>Parametry

*OutIt*\
Typ iteratora danych wyjściowych.

*określoną*\
Strumień wyjściowy, do którego będą zapisywane dane.

*FMT*\
Ciąg formatu.

*znaczników*\
Flagi formatu.

### <a name="remarks"></a>Uwagi

Każda funkcja członkowska generuje sformatowany tekst w kontrolce formatu *FMT*. Pierwsza funkcja elementu członkowskiego zapisuje sformatowany tekst do sekwencji zdefiniowanej przez jej argument *out* i zwraca wartość *out*. Druga funkcja elementu członkowskiego zwraca obiekt ciągu, który zawiera kopię sformatowanego tekstu.

W celu wygenerowania sformatowanego tekstu. tekst literału w ciągu formatu jest zwykle kopiowany do sekwencji docelowej. Każda sekwencja unikowa w ciągu formatu jest zastępowana przez tekst, który reprezentuje. Szczegóły dotyczące kopiowania i wymiany są kontrolowane przez flagi formatu przekazane do funkcji.

## <a name="get_allocator"></a>match_results::get_allocator

Zwraca przechowywany program przydzielający.

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca kopię obiektu alokatora używanego przez `*this` program w celu przydzielenia jego `sub_match` obiektów.

## <a name="iterator"></a>match_results:: iterator

Typ iteratora dla podpasowań.

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może działać jako Iterator dostępu swobodnego dla kontrolowanej sekwencji.

## <a name="length"></a>match_results:: length

Zwraca długość poddopasowania.

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*Sub*\
Indeks poddopasowania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `(*this)[sub].length()`wartość.

## <a name="match_results"></a>match_results::match_results

Konstruuje obiekt.

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>Parametry

*alokacj*\
Obiekt alokatora, który ma być przechowywany.

*Kliknij*\
Obiekt match_results do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje `match_results` obiekt, który nie zawiera żadnych pododpowiedników. Drugi Konstruktor konstruuje `match_results` obiekt, który jest kopią *prawej*.

## <a name="max_size"></a>match_results::max_size

Pobiera największą liczbę podpasowań.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca długość najdłuższej sekwencji, którą obiekt może kontrolować.

## <a name="op_eq"></a>match_results:: operator =

Skopiuj obiekt match_results.

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt match_results do skopiowania.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje sekwencję `*this` z funkcją z kopią sekwencji kontrolowanej przez *prawo*.

## <a name="op_at"></a>match_results:: operator []

Dostęp do podobiektu.

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>Parametry

*Azotan*\
Indeks poddopasowania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca odwołanie do elementu *n* kontrolowanej sekwencji lub odwołanie do pustego `sub_match` obiektu, jeśli `size() <= n` lub jeśli grupa przechwytywania *n* nie była częścią dopasowania.

## <a name="position"></a>match_results::p ozycja

Pobierz początkowe przesunięcie podgrupy.

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*Sub*\
Indeks poddopasowania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `std::distance(prefix().first, (*this)[sub].first)`, czyli odległość od pierwszego znaku w sekwencji docelowej do pierwszego znaku w dopasowań wskazywanym przez element `n` w kontrolowanej sekwencji.

## <a name="prefix"></a>match_results::p refix

Pobiera sekwencję przed pierwszym poddopasowaniem.

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca odwołanie do obiektu typu `sub_match<BidIt>` , który wskazuje na sekwencję znaków rozpoczynającą się na początku sekwencji docelowej i kończącą się na `(*this)[0].first`, czyli wskazuje na tekst poprzedzający dopasowaną podsekwencję.

## <a name="reference"></a>match_results:: Reference

Typ odwołania do elementu.

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem typu `const_reference`.

## <a name="size"></a>match_results:: size

Liczy liczbę podpasowań.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca jeden więcej niż liczba grup przechwytywania w wyrażeniu regularnym użytym do wyszukiwania lub zero, jeśli nie wykonano wyszukiwania.

## <a name="size_type"></a>match_results::size_type

Typ liczby poddopasowywania.

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem typu `Alloc::size_type`.

## <a name="str"></a>match_results:: str

Zwraca poddopasowanie.

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*Sub*\
Indeks poddopasowania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `string_type((*this)[sub])`wartość.

## <a name="string_type"></a>match_results::string_type

Typ ciągu.

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem typu `basic_string<char_type>`.

## <a name="suffix"></a>match_results:: sufiks

Pobiera sekwencję po ostatnim dopasowań.

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca odwołanie do obiektu typu `sub_match<BidIt>` , który wskazuje na sekwencję znaków, która rozpoczyna się od `(*this)[size() - 1].second` i kończy się na końcu sekwencji docelowej, czyli wskazuje na tekst, który następuje po dopasowanej podsekwencji.

## <a name="swap"></a>match_results:: swap

Zamienia dwa obiekty match_results.

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt match_results do zamiany.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia zawartość `*this` i *bezpośrednio* w stałym czasie i nie zgłasza wyjątków.

## <a name="value_type"></a>match_results::value_type

Typ poddopasowania.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Uwagi

Element typedef jest synonimem typu `sub_match<BidIt>`.

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)

---
title: match_results — Klasa
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: 31154a38f8bbcb879fd871f1eb1bf5a4b15af79b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371019"
---
# <a name="match_results-class"></a>match_results — Klasa

Przechowuje sekwencję podmeczów.

## <a name="syntax"></a>Składnia

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>Parametry

*OfertaIt*\
Typ iteratora dla podmeczów.

*Alloc*\
Typ alokatora do zarządzania pamięcią.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który steruje niemodyfikowalnym sekwencją elementów typu `sub_match<BidIt>` generowanych przez wyszukiwanie wyrażeń regularnych. Każdy element wskazuje podsekwencję, która odpowiadała grupie przechwytywania odpowiadającej tej elemencie.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Match_results](#match_results)|Konstruuje obiekt.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ alokatora do zarządzania pamięcią.|
|[Char_type](#char_type)|Typ elementu.|
|[const_iterator](#const_iterator)|Typ iteratora konseplanatora dla podmeczów.|
|[const_reference](#const_reference)|Typ odwołania const elementu.|
|[difference_type](#difference_type)|Typ różnicy iteratora.|
|[Sterująca](#iterator)|Typ iteratora dla podmeczów.|
|[Odwołanie](#reference)|Typ odwołania do elementu.|
|[size_type](#size_type)|Typ liczby podmeczów.|
|[string_type](#string_type)|Typ ciągu.|
|[value_type](#value_type)|Typ podmeczu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Rozpocząć](#begin)|Wyznacza początek sekwencji podmeczu.|
|[Pusty](#empty)|Testy dla nie podmeczów.|
|[Końcu](#end)|Wyznacza koniec sekwencji podmeczu.|
|[Formacie](#format)|Poddopasowania formatów.|
|[Get_allocator](#get_allocator)|Zwraca przechowywany alokator.|
|[Długość](#length)|Zwraca długość podmeczu.|
|[Max_size](#max_size)|Pobiera największą liczbę podmeczów.|
|[Pozycji](#position)|Pobierz przesunięcie początkowe podgrupy.|
|[Prefiks](#prefix)|Pobiera sekwencji przed pierwszym podmecz.|
|[Rozmiar](#size)|Zlicza liczbę podmeczów.|
|[Str](#str)|Zwraca podmecz.|
|[Sufiks](#suffix)|Pobiera sekwencji po ostatnim podmecz.|
|[Wymiany](#swap)|Zamienia dwa match_results obiekty.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Skopiuj obiekt match_results.|
|[Operator\[\]](#op_at)|Dostęp do podobiekty.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> regex

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

## <a name="match_resultsallocator_type"></a><a name="allocator_type"></a>match_results::allocator_type

Typ alokatora do zarządzania pamięcią.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem argumentu *szablonu Alloc*.

## <a name="match_resultsbegin"></a><a name="begin"></a>match_results::begin

Wyznacza początek sekwencji podmeczu.

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iteratora dostępu losowego, który wskazuje na pierwszy element sekwencji (lub tuż za końcem pustej sekwencji).

## <a name="match_resultschar_type"></a><a name="char_type"></a>match_results::char_type

Typ elementu.

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem typu `iterator_traits<BidIt>::value_type`, który jest typem elementu sekwencji znaków, który został przeszukany.

## <a name="match_resultsconst_iterator"></a><a name="const_iterator"></a>match_results::const_iterator

Typ iteratora konseplanatora dla podmeczów.

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typedef opisuje obiekt, który może służyć jako stały iterator dostępu losowego dla kontrolowanej sekwencji.

## <a name="match_resultsconst_reference"></a><a name="const_reference"></a>match_results::const_reference

Typ odwołania const elementu.

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

Typedef opisuje obiekt, który może służyć jako stałe odwołanie do elementu kontrolowanej sekwencji.

## <a name="match_resultsdifference_type"></a><a name="difference_type"></a>match_results::d00_typ

Typ różnicy iteratora.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem typu; `iterator_traits<BidIt>::difference_type` opisuje obiekt, który może reprezentować różnicę między dowolnymi dwoma iteratorami, które wskazują na elementy kontrolowanej sekwencji.

## <a name="match_resultsempty"></a><a name="empty"></a>match_results::empty

Testy dla nie podmeczów.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość true tylko wtedy, gdy wyszukiwanie wyrażeń regularnych nie powiodło się.

## <a name="match_resultsend"></a><a name="end"></a>match_results::end

Wyznacza koniec sekwencji podmeczu.

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iteratora, który wskazuje tuż za końcem sekwencji.

## <a name="match_resultsformat"></a><a name="format"></a>match_results::format

Poddopasowania formatów.

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>Parametry

*OutIt (OutIt)*\
Typ iteratora danych wyjściowych.

*na zewnątrz*\
Strumień wyjściowy, do którego będą zapisywane dane.

*Fmt*\
Ciąg formatu.

*Flagi*\
Flagi formatu.

### <a name="remarks"></a>Uwagi

Każda funkcja elementu członkowskiego generuje sformatowany tekst pod kontrolą formatu *fmt*. Funkcja pierwszego elementu członkowskiego zapisuje sformatowany tekst do sekwencji zdefiniowanej przez jego *argument* i *zwraca*. Funkcja drugiego elementu członkowskiego zwraca obiekt ciągu zawierający kopię sformatowanego tekstu.

Aby wygenerować sformatowany tekst. tekst dosłowny w ciągu formatu jest zwykle kopiowany do sekwencji docelowej. Każda sekwencja unikowa w ciągu formatu jest zastępowana przez tekst, który reprezentuje. Szczegóły dotyczące kopiowania i wymiany są kontrolowane przez flagi formatu przekazane do funkcji.

## <a name="match_resultsget_allocator"></a><a name="get_allocator"></a>match_results::get_allocator

Zwraca przechowywany alokator.

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca kopię obiektu alokatora używanego `*this` do przydzielenia jego `sub_match` obiektów.

## <a name="match_resultsiterator"></a><a name="iterator"></a>match_results::iterator

Typ iteratora dla podmeczów.

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako iterator dostępu losowego dla kontrolowanej sekwencji.

## <a name="match_resultslength"></a><a name="length"></a>match_results::długość

Zwraca długość podmeczu.

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*Sub*\
Indeks podmeczu.

### <a name="remarks"></a>Uwagi

Funkcja elementu `(*this)[sub].length()`członkowskiego zwraca .

## <a name="match_resultsmatch_results"></a><a name="match_results"></a>match_results::match_results

Konstruuje obiekt.

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>Parametry

*Alloc*\
Obiekt alokatora, który ma być przechowywany.

*Prawo*\
Match_results do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor tworzy `match_results` obiekt, który nie posiada żadnych podmeczów. Drugi konstruktor tworzy `match_results` obiekt, który jest kopią *prawej*.

## <a name="match_resultsmax_size"></a><a name="max_size"></a>match_results::max_size

Pobiera największą liczbę podmeczów.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca długość najdłuższej sekwencji, którą obiekt może kontrolować.

## <a name="match_resultsoperator"></a><a name="op_eq"></a>match_results::operator=

Skopiuj obiekt match_results.

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Match_results do skopiowania.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje sekwencję kontrolowaną przez `*this` kopię sekwencji kontrolowanej przez *prawo*.

## <a name="match_resultsoperator"></a><a name="op_at"></a>match_results::operator[]

Dostęp do podobiekty.

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>Parametry

*N*\
Indeks podmeczu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do elementu *n* kontrolowanej sekwencji lub odwołanie do pustego `sub_match` obiektu, jeśli `size() <= n` lub jeśli grupa przechwytywania *n* nie była częścią dopasowania.

## <a name="match_resultsposition"></a><a name="position"></a>match_results::psyliż

Pobierz przesunięcie początkowe podgrupy.

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*Sub*\
Indeks podmeczu.

### <a name="remarks"></a>Uwagi

Funkcja elementu `std::distance(prefix().first, (*this)[sub].first)`członkowskiego zwraca , czyli odległość od pierwszego znaku w sekwencji docelowej do pierwszego `n` znaku w podmecz wskazanym przez element kontrolowanej sekwencji.

## <a name="match_resultsprefix"></a><a name="prefix"></a>match_results::prefix

Pobiera sekwencji przed pierwszym podmecz.

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do `sub_match<BidIt>` obiektu typu, który wskazuje sekwencję znaków, która `(*this)[0].first`rozpoczyna się na początku sekwencji docelowej i kończy się na , to znaczy, wskazuje na tekst, który poprzedza dopasowaną podsekwencję.

## <a name="match_resultsreference"></a><a name="reference"></a>match_results::odwołanie

Typ odwołania do elementu.

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem typu `const_reference`.

## <a name="match_resultssize"></a><a name="size"></a>match_results::size

Zlicza liczbę podmeczów.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca jeden więcej niż liczba grup przechwytywania w wyrażeniu regularnym, który został użyty do wyszukiwania lub zero, jeśli nie przeprowadzono wyszukiwania.

## <a name="match_resultssize_type"></a><a name="size_type"></a>match_results::size_type

Typ liczby podmeczów.

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem typu `Alloc::size_type`.

## <a name="match_resultsstr"></a><a name="str"></a>match_results::str

Zwraca podmecz.

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*Sub*\
Indeks podmeczu.

### <a name="remarks"></a>Uwagi

Funkcja elementu `string_type((*this)[sub])`członkowskiego zwraca .

## <a name="match_resultsstring_type"></a><a name="string_type"></a>match_results::string_type

Typ ciągu.

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem typu `basic_string<char_type>`.

## <a name="match_resultssuffix"></a><a name="suffix"></a>match_results::sufiks

Pobiera sekwencji po ostatnim podmecz.

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do `sub_match<BidIt>` obiektu typu, który wskazuje `(*this)[size() - 1].second` sekwencję znaków, która rozpoczyna się na końcu sekwencji docelowej i kończy się na końcu sekwencji docelowej, czyli wskazuje na tekst, który następuje po dopasowanej podsekwencji.

## <a name="match_resultsswap"></a><a name="swap"></a>match_results::swap

Zamienia dwa match_results obiekty.

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>Parametry

*Prawo*\
Obiekt match_results do wymiany.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia `*this` zawartość i *prawo* w stałym czasie i nie zgłasza wyjątków.

## <a name="match_resultsvalue_type"></a><a name="value_type"></a>match_results::value_type

Typ podmeczu.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem typu `sub_match<BidIt>`.

## <a name="see-also"></a>Zobacz też

[\<>regex](../standard-library/regex.md)

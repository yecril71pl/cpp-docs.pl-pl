---
title: match_results — Klasa
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: bfb1a8b779f741360b406d9a5c24a36bca5e54f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662517"
---
# <a name="matchresults-class"></a>match_results — Klasa

Zawiera sekwencję poddopasowania.

## <a name="syntax"></a>Składnia

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>Parametry

*BidIt*<br/>
Typ iteratora poddopasowania.

*Alokacji*<br/>
Typ alokatora do zarządzania pamięcią.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który kontroluje uniemożliwiającym sekwencje elementów typu `sub_match<BidIt>` generowane przez wyszukiwanie wyrażenia regularnego. Każdy element wskazuje podsekwencję, która pasuje do grupy przechwytywania, odpowiadający tego elementu.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[match_results](#match_results)|Tworzy obiekt.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ alokatora do zarządzania pamięcią.|
|[char_type](#char_type)|Typ elementu.|
|[const_iterator](#const_iterator)|Typ iteratora stałych dla poddopasowania.|
|[const_reference](#const_reference)|Typ odwołania do elementu const.|
|[difference_type](#difference_type)|Typ różnicy iteratora.|
|[iterator](#iterator)|Typ iteratora poddopasowania.|
|[Odwołanie](#reference)|Typ odwołania do elementu.|
|[size_type](#size_type)|Typ liczby poddopasowanie.|
|[string_type](#string_type)|Typ ciągu.|
|[value_type](#value_type)|Typ poddopasowanie.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[begin](#begin)|Określa początek poddopasowanie sekwencji.|
|[pusty](#empty)|Testuje pod kątem nie poddopasowania.|
|[koniec](#end)|Określa koniec poddopasowanie sekwencji.|
|[Format](#format)|Poddopasowania formatów.|
|[get_allocator](#get_allocator)|Zwraca przechowywaną alokatora.|
|[Długość](#length)|Zwraca długość poddopasowanie.|
|[max_size](#max_size)|Pobiera największą liczbę poddopasowania.|
|[Stanowisko](#position)|Pobierz początkowe przesunięcie podgrupy.|
|[Prefiks](#prefix)|Pobiera sekwencję przed pierwszym poddopasowanie.|
|[Rozmiar](#size)|Zlicza poddopasowania.|
|[str](#str)|Zwraca poddopasowanie.|
|[suffix](#suffix)|Pobiera sekwencję po ostatnie poddopasowanie.|
|[swap](#swap)|Zamienia dwa obiekty match_results —.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Kopiowanie obiektu match_results —.|
|[Operator]](#op_at)|Dostęp do podobiektów.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyrażenia regularnego >

**Namespace:** standardowe

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

## <a name="allocator_type"></a>  match_results::allocator_type

Typ alokatora do zarządzania pamięcią.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem dla argumentu szablonu *alokacji*.

## <a name="begin"></a>  match_results::BEGIN

Określa początek poddopasowanie sekwencji.

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator dostępu losowego, który wskazuje na pierwszy element sekwencji (lub tuż za koniec pustej sekwencji).

## <a name="char_type"></a>  match_results::char_type

Typ elementu.

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem typu `iterator_traits<BidIt>::value_type`, który jest typem elementu sekwencji znaków, który został przeszukane.

## <a name="const_iterator"></a>  match_results::const_iterator

Typ iteratora stałych dla poddopasowania.

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>Uwagi

Typedef opisuje obiekt, który może służyć jako stały iterator dostępu swobodnego dla kontrolowanej sekwencji.

## <a name="const_reference"></a>  match_results::const_reference

Typ odwołania do elementu const.

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

Typedef opisuje obiekt, który może służyć jako stałe odwołanie do elementu w kontrolowanej sekwencji.

## <a name="difference_type"></a>  match_results::difference_type

Typ różnicy iteratora.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem typu `iterator_traits<BidIt>::difference_type`; opisuje obiekt, który może reprezentować różnicę między dwoma iteratorami, które wskazują na elementy kontrolowanej sekwencji.

## <a name="empty"></a>  match_results::Empty

Testuje pod kątem nie poddopasowania.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość true tylko wtedy, gdy wyszukiwanie wyrażenia regularnego nie powiodło się.

## <a name="end"></a>  match_results::end

Określa koniec poddopasowanie sekwencji.

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca iterator, który wskazuje tuż za koniec sekwencji.

## <a name="format"></a>  match_results::format

Poddopasowania formatów.

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>Parametry

*OutIt*<br/>
Typ iteratora danych wyjściowych.

*out*<br/>
Strumień wyjściowy, do którego będą zapisywane dane.

*FMT*<br/>
Ciąg formatu.

*flagi*<br/>
Flagi formatu.

### <a name="remarks"></a>Uwagi

Każda funkcja elementu członkowskiego generuje sformatowany tekst pod kontrolą formatu *fmt*. Pierwsza funkcja elementu członkowskiego zapisuje sformatowany tekst do sekwencji zdefiniowanej przez jej argument *się* i zwraca *się*. Druga funkcja elementu członkowskiego zwraca obiekt ciągu, który zawiera kopię sformatowanego tekstu.

Aby wygenerować sformatowany tekst. tekst dosłowny w ciągu formatu jest zwyczajnie kopiowany do sekwencji docelowej. Każda sekwencja unikowa w ciągu formatu jest zastępowana przez tekst, który reprezentuje. Szczegóły dotyczące kopiowania i wymiany są kontrolowane przez flagi formatu przekazane do funkcji.

## <a name="get_allocator"></a>  match_results::get_allocator

Zwraca przechowywaną alokatora.

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca kopię obiektu programu przydzielania posługują się `*this` przydzielić jej `sub_match` obiektów.

## <a name="iterator"></a>  match_results::iterator

Typ iteratora poddopasowania.

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako iterator dostępu swobodnego dla kontrolowanej sekwencji.

## <a name="length"></a>  match_results::length

Zwraca długość poddopasowanie.

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*sub*<br/>
Indeks poddopasowanie.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `(*this)[sub].length()`.

## <a name="match_results"></a>  match_results::match_results

Tworzy obiekt.

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>Parametry

*Alokacji*<br/>
Obiekt alokatora, który ma być przechowywany.

*right*<br/>
Match_results — obiekt do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje `match_results` obiekt, który przechowuje nie poddopasowania. Drugi Konstruktor konstruuje `match_results` obiekt, który jest kopią *prawo*.

## <a name="max_size"></a>  match_results::max_size

Pobiera największą liczbę poddopasowania.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca długość najdłuższej sekwencji, która może kontrolować obiekt.

## <a name="op_eq"></a>  match_results::operator =

Kopiowanie obiektu match_results —.

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Match_results — obiekt do skopiowania.

### <a name="remarks"></a>Uwagi

Operator składowy zastępuje sekwencji kontrolowanej przez `*this` kopię sekwencji kontrolowanej przez *prawo*.

## <a name="op_at"></a>  [] match_results::operator

Dostęp do podobiektów.

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>Parametry

*N*<br/>
Indeks poddopasowanie.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do elementu *n* kontrolowanej sekwencji lub odwołanie do pustego `sub_match` obiektu, jeśli `size() <= n` lub grupę przechwytywania, jeśli *n* nie było częścią dopasowanie.

## <a name="position"></a>  match_results::Position

Pobierz początkowe przesunięcie podgrupy.

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*sub*<br/>
Indeks poddopasowanie.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `std::distance(prefix().first, (*this)[sub].first)`, czyli odległość od pierwszego znaku w sekwencji docelowej, do pierwszego znaku w poddopasowanie wskazywany przez element `n` kontrolowanej sekwencji.

## <a name="prefix"></a>  match_results::prefix

Pobiera sekwencję przed pierwszym poddopasowanie.

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do obiektu typu `sub_match<BidIt>` który wskazuje na sekwencję znaków, która rozpoczyna się na początku sekwencji docelowej, a kończy się na `(*this)[0].first`, oznacza to, że wskazuje on poprzedzająca podsekwencję, dopasowany tekst.

## <a name="reference"></a>  match_results::Reference

Typ odwołania do elementu.

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem typu `const_reference`.

## <a name="size"></a>  match_results::size

Zlicza poddopasowania.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Uwagi

Element członkowski funkcja zwraca jeden więcej niż liczba grup przechwytywania w wyrażeniu regularnym, który był używany podczas wyszukiwania lub zero, jeśli wyszukiwanie nie zostały wprowadzone.

## <a name="size_type"></a>  match_results::size_type

Typ liczby poddopasowanie.

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem typu `Alloc::size_type`.

## <a name="str"></a>  match_results::str

Zwraca poddopasowanie.

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*sub*<br/>
Indeks poddopasowanie.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `string_type((*this)[sub])`.

## <a name="string_type"></a>  match_results::STRING_TYPE

Typ ciągu.

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem typu `basic_string<char_type>`.

## <a name="suffix"></a>  match_results::suffix

Pobiera sekwencję po ostatnie poddopasowanie.

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do obiektu typu `sub_match<BidIt>` który wskazuje na sekwencję znaków, która rozpoczyna się od `(*this)[size() - 1].second` i kończy się na końcu sekwencji docelowej, oznacza to, że wskazuje tekst, który następuje po podsekwencji dopasowany.

## <a name="swap"></a>  match_results::swap

Zamienia dwa obiekty match_results —.

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>Parametry

*right*<br/>
Match_results — obiekt, który można zamienić za pomocą.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia zawartości `*this` i *prawo* w czasie stała i nie zgłasza wyjątków.

## <a name="value_type"></a>  match_results::value_type

Typ poddopasowanie.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem typu `sub_match<BidIt>`.

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)<br/>

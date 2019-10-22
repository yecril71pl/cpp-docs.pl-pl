---
title: sub_match — Klasa
ms.date: 09/10/2018
f1_keywords:
- regex/std::sub_match
- regex/std::sub_match::matched
- regex/std::sub_match::compare
- regex/std::sub_match::length
- regex/std::sub_match::str
- regex/std::sub_match::difference_type
- regex/std::sub_match::iterator
- regex/std::sub_match::value_type
helpviewer_keywords:
- std::sub_match [C++]
- std::sub_match [C++], matched
- std::sub_match [C++], compare
- std::sub_match [C++], length
- std::sub_match [C++], str
- std::sub_match [C++], difference_type
- std::sub_match [C++], iterator
- std::sub_match [C++], value_type
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
ms.openlocfilehash: 776dfe67367b932435f76af94880111cad61341d
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685844"
---
# <a name="sub_match-class"></a>sub_match — Klasa

Opisuje poddopasowanie.

## <a name="syntax"></a>Składnia

```cpp
template <class BidIt>
class sub_match
    : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>Parametry

*BidIt* \
Typ iteratora dla podpasowań.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który wyznacza sekwencję znaków, które pasują do grupy przechwytywania w wywołaniu [regex_match](../standard-library/regex-functions.md#regex_match) lub [regex_search](../standard-library/regex-functions.md#regex_search). Obiekty typu [match_results](../standard-library/match-results-class.md) zawierają tablicę tych obiektów, jedną dla każdej grupy przechwytywania w wyrażeniu regularnym, która została użyta w wyszukiwaniu.

Jeśli grupa przechwytywania nie była zgodna z elementem członkowskim danych obiektu `matched` ma wartość false, a dwa Iteratory `first` i `second` (dziedziczone z `std::pair` podstawowego) są równe. Jeśli grupa przechwytywania została dopasowana, `matched` ma wartość true, iterator `first` wskazuje na pierwszy znak w sekwencji docelowej pasującej do grupy przechwytywania, a iterator `second` punkty po ostatnim znaku w sekwencji docelowej, która pasowała Grupa przechwytywania. Należy zauważyć, że dla elementu członkowskiego o zerowej długości, `matched` ma wartość true, dwa Iteratory będą równe, a oba będą wskazywały na pozycję dopasowania.

Dopasowanie o zerowej długości może wystąpić, gdy grupa przechwytywania składa się wyłącznie z potwierdzenia lub powtórzenia, które dopuszcza zero powtórzeń. Na przykład:

"^" pasuje do sekwencji docelowej "a"; Obiekt `sub_match` odpowiadający grupie przechwytywania 0 przechowuje Iteratory wskazujące na pierwszy znak w sekwencji.

"b (a *) b" pasuje do sekwencji docelowej "bb"; Obiekt `sub_match` odpowiadający grupie przechwytywania 1 przechowuje Iteratory, które wskazują drugi znak w sekwencji.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[difference_type](#difference_type)|Typ różnicy iteratora.|
|[Iterator](#iterator)|Typ iteratora.|
|[value_type](#value_type)|Typ elementu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[porównaniu](#compare)|Porównaj poddopasowanie z sekwencją.|
|[Długość](#length)|Zwraca długość poddopasowania.|
|[uzgodni](#matched)|Wskazuje, czy dopasowanie zakończyło się pomyślnie.|
|[str](#str)|Konwertuje poddopasowanie na ciąg.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator basic_string < value_type >](#op_basic_string_lt_value_type_gt)|Rzutuje poddopasowanie na ciąg.|

## <a name="example"></a>Przykład

```cpp
// std__regex__sub_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;

    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);
    std::cout << "difference == " << dif << std::endl;

    std::csub_match::iterator first = sub.first;
    std::csub_match::iterator last = sub.second;
    std::cout << "range == " << std::string(first, last)
        << std::endl;
    std::cout << "string == " << sub << std::endl;

    std::csub_match::value_type const *ptr = "aab";
    std::cout << "compare(\"aab\") == "
        << sub.compare(ptr) << std::endl;
    std::cout << "compare(string) == "
        << sub.compare(std::string("AAA")) << std::endl;
    std::cout << "compare(sub) == "
        << sub.compare(sub) << std::endl;

    return (0);
    }
```

```Output
matched == true
length == 3
difference == 3
range == aaa
string == aaa
compare("aab") == -1
compare(string) == 1
compare(sub) == 0
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<regex >

**Przestrzeń nazw:** std

## <a name="compare"></a>sub_match:: Compare

Porównaj poddopasowanie z sekwencją.

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parametry

*prawa* \
Poddopasowanie do porównania.

*str* \
Ciąg do porównania.

\ *PTR*
Sekwencja zakończona wartością null do porównania.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska porównuje dopasowaną sekwencję `[first, second)` do dopasowanej `[right.first, right.second)` sekwencji. Druga funkcja członkowska porównuje dopasowaną sekwencję `[first, second)` do `[right.begin(), right.end())` sekwencji znaków. Trzecia funkcja członkowska porównuje dopasowaną sekwencję `[first, second)` do `[right, right + std::char_traits<value_type>::length(right))` sekwencji znaków.

Każda funkcja zwraca:

wartość ujemna, jeśli pierwsza różna wartość w dopasowanej sekwencji porównuje mniej niż odpowiadający element w sekwencji operandu (zgodnie z definicją `std::char_traits<value_type>::compare`) lub jeśli dwa mają wspólny prefiks, ale sekwencja docelowa jest dłuższa

zero, jeśli dwa porównania są równe elementu przez element i mają tę samą długość

wartość dodatnia w przeciwnym razie

## <a name="difference_type"></a>sub_match::d ifference_type

Typ różnicy iteratora.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Element typedef jest synonimem dla `iterator_traits<BidIt>::difference_type`.

## <a name="iterator"></a>sub_match:: iterator

Typ iteratora.

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>Uwagi

Element typedef jest synonimem dla argumentu typu szablonu `Bidit`.

## <a name="length"></a>sub_match:: length

Zwraca długość poddopasowania.

```cpp
difference_type length() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca długość dopasowanej sekwencji lub zero, jeśli nie ma dopasowanej sekwencji.

## <a name="matched"></a>sub_match:: MATCHED

Wskazuje, czy dopasowanie zakończyło się pomyślnie.

```cpp
bool matched;
```

### <a name="remarks"></a>Uwagi

Składowa **ma wartość true** tylko wtedy, gdy grupa przechwytywania skojarzona z `*this` była częścią dopasowania wyrażenia regularnego.

## <a name="op_basic_string_lt_value_type_gt"></a>sub_match:: operator basic_string &lt;value_type &gt;

Rzutuje poddopasowanie na ciąg.

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `str()`.

## <a name="str"></a>sub_match:: str

Konwertuje poddopasowanie na ciąg.

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `basic_string<value_type>(first, second)`.

## <a name="value_type"></a>sub_match::value_type

Typ elementu.

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Element typedef jest synonimem dla `iterator_traits<BidIt>::value_type`.

## <a name="see-also"></a>Zobacz także

[\<regex >](../standard-library/regex.md) \
[sub_match](../standard-library/sub-match-class.md)

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
ms.openlocfilehash: 460f79fe0f23643fafcebb64aecf2988bdb0debe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376587"
---
# <a name="sub_match-class"></a>sub_match — Klasa

Opisuje podmecz.

## <a name="syntax"></a>Składnia

```cpp
template <class BidIt>
class sub_match
    : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>Parametry

*OfertaIt*\
Typ iteratora dla podmeczów.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który wyznacza sekwencję znaków, które pasowały do grupy przechwytywania w wywołaniu [regex_match](../standard-library/regex-functions.md#regex_match) lub [regex_search](../standard-library/regex-functions.md#regex_search). Obiekty typu [match_results Class](../standard-library/match-results-class.md) posiadają tablicę tych obiektów, po jednej dla każdej grupy przechwytywania w wyrażeniu regularnym, który został użyty w wyszukiwaniu.

Jeśli grupa przechwytywania nie została dopasowana `matched` element członkowski danych obiektu zawiera `first` `second` false, a dwa `std::pair`iteratory i (dziedziczone z podstawy) są równe. Jeśli grupa przechwytywania została `matched` dopasowana, true, `first` iterator wskazuje na pierwszy znak w sekwencji docelowej, `second` który pasował do grupy przechwytywania, a iterator wskazuje jedną pozycję obok ostatniego znaku w sekwencji docelowej, który pasował do grupy przechwytywania. Należy zauważyć, że dla dopasowania `matched` o zerowej długości element członkowski posiada wartość true, dwa iteratory będą równe i oba wskazują na położenie dopasowania.

Dopasowanie o zerowej długości może wystąpić, gdy grupa przechwytywania składa się wyłącznie z potwierdzenia lub powtórzenia, które umożliwia powtórzenie zerowe. Przykład:

"^" pasuje do sekwencji docelowej "a"; obiekt `sub_match` odpowiadający przechwytywaniu grupy 0 przechowuje iteratory, które wskazują na pierwszy znak w sekwencji.

"b(a*)b" pasuje do docelowej sekwencji "bb"; obiekt `sub_match` odpowiadający przechwytywaniu grupy 1 zawiera iteratory, które wskazują na drugi znak w sekwencji.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[difference_type](#difference_type)|Typ różnicy iteratora.|
|[Sterująca](#iterator)|Typ iteratora.|
|[value_type](#value_type)|Typ elementu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Porównać](#compare)|Porównaj podmecz z sekwencją.|
|[Długość](#length)|Zwraca długość podmeczu.|
|[Dopasowane](#matched)|Wskazuje, czy dopasowanie powiodło się.|
|[Str](#str)|Konwertuje podmecz na ciąg.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[basic_string<value_type>operatora](#op_basic_string_lt_value_type_gt)|Rzutuje podmecz na ciąg.|

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

**Nagłówek:** \<> regex

**Przestrzeń nazw:** std

## <a name="sub_matchcompare"></a><a name="compare"></a>sub_match::porównaj

Porównaj podmecz z sekwencją.

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Podmecz do porównania.

*Str*\
Ciąg do porównania.

*Ptr*\
Sekwencja zakończona z wartością null do porównania.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego porównuje `[first, second)` dopasowana sekwencja `[right.first, right.second)`z dopasowanym sekwencją . Druga funkcja elementu członkowskiego porównuje `[first, second)` dopasowana sekwencja z sekwencją `[right.begin(), right.end())`znaków . Funkcja trzeciego elementu członkowskiego porównuje `[first, second)` dopasowana sekwencja z sekwencją `[right, right + std::char_traits<value_type>::length(right))`znaków .

Każda funkcja zwraca:

wartość ujemna, jeśli pierwsza inna wartość w dopasowanej sekwencji porównuje mniej niż odpowiedni `std::char_traits<value_type>::compare`element w sekwencji operandu (jak określono przez ), lub jeśli obie mają wspólny prefiks, ale sekwencja docelowa jest dłuższa

zero, jeśli dwa porównać równy element po elemencie i mają taką samą długość

wartość dodatnią w przeciwnym razie

## <a name="sub_matchdifference_type"></a><a name="difference_type"></a>sub_match::d00_typ

Typ różnicy iteratora.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem `iterator_traits<BidIt>::difference_type`.

## <a name="sub_matchiterator"></a><a name="iterator"></a>sub_match::iterator

Typ iteratora.

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem argumentu `Bidit`typu szablonu .

## <a name="sub_matchlength"></a><a name="length"></a>sub_match::długość

Zwraca długość podmeczu.

```cpp
difference_type length() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca długość dopasowanej sekwencji lub zero, jeśli nie było dopasowanej sekwencji.

## <a name="sub_matchmatched"></a><a name="matched"></a>sub_match::dopasowane

Wskazuje, czy dopasowanie powiodło się.

```cpp
bool matched;
```

### <a name="remarks"></a>Uwagi

Element członkowski **ma wartość true** tylko `*this` wtedy, gdy grupa przechwytywania skojarzone z był częścią dopasowania wyrażenia regularnego.

## <a name="sub_matchoperator-basic_stringltvalue_typegt"></a><a name="op_basic_string_lt_value_type_gt"></a>sub_match::operator basic_string&lt;value_type&gt;

Rzutuje podmecz na ciąg.

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>Uwagi

Operator elementu `str()`członkowskiego zwraca .

## <a name="sub_matchstr"></a><a name="str"></a>sub_match::str

Konwertuje podmecz na ciąg.

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu `basic_string<value_type>(first, second)`członkowskiego zwraca .

## <a name="sub_matchvalue_type"></a><a name="value_type"></a>sub_match::value_type

Typ elementu.

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem `iterator_traits<BidIt>::value_type`.

## <a name="see-also"></a>Zobacz też

[\<>regex](../standard-library/regex.md)\
[sub_match](../standard-library/sub-match-class.md)

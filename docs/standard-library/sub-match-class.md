---
title: sub_match — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::sub_match
- regex/std::sub_match::matched
- regex/std::sub_match::compare
- regex/std::sub_match::length
- regex/std::sub_match::str
- regex/std::sub_match::difference_type
- regex/std::sub_match::iterator
- regex/std::sub_match::value_type
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 132498c5773e4cce1fd178573698b62e874dda48
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691617"
---
# <a name="submatch-class"></a>sub_match — Klasa

W tym artykule opisano poddopasowanie.

## <a name="syntax"></a>Składnia

```cpp
template <class BidIt>
class sub_match
 : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>Parametry

*BidIt*  
 Typ iteratora poddopasowania.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który określa sekwencję znaków pasujących do grupy przechwytywania w wywołaniu [regex_match —](../standard-library/regex-functions.md#regex_match) lub [regex_search —](../standard-library/regex-functions.md#regex_search). Obiekty typu [match_results, klasa](../standard-library/match-results-class.md) przechowują tablicę tych obiektów, po jednym dla każdej grupy przechwytywania w wyrażeniu regularnym, który został użyty w wyszukiwaniu.

Jeśli grupa przechwytywania nie było dopasować element członkowski danych obiektu `matched` przechowuje wartość FAŁSZ i dwoma iteratorami `first` i `second` (dziedziczone od podstawy `std::pair`) są takie same. Jeśli zostały dopasowane do grupy przechwytywania, `matched` ma wartość true, przechowuje iterator `first` wskazuje na pierwszy znak w sekwencji docelowej, który pasuje do grupy przechwytywania, a iterator `second` wskazuje jedną pozycję poza ostatnim znakiem w elemencie docelowym Sekwencja dopasowanym do grupy przechwytywania. Należy zauważyć, że o zerowej długości dopasowania elementu członkowskiego `matched` posiada wartość true, dwa Iteratory są równe, a oba będą wskazywały na pozycji dopasowania.

Dopasowanie o zerowej długości może wystąpić, gdy grupa przechwytywania składa się wyłącznie z potwierdzenie lub z powtórzenia umożliwiająca Brak powtórzeń. Na przykład:

"^" pasuje do sekwencji docelowej ";" `sub_match` obiekt odpowiadający 0 grupę przechwytywania zawiera Iteratory zarówno wskaż pierwszego znaku w sekwencji.

"b(a*) b" pasuje do sekwencji docelowej "bb"; `sub_match` obiekt odpowiadający grupę przechwytywania 1 zawiera Iteratory zarówno wskaż drugim znaku w sekwencji.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[difference_type](#difference_type)|Typ różnicy iteratora.|
|[iterator](#iterator)|Typ iteratora.|
|[value_type](#value_type)|Typ elementu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Porównanie](#compare)|Porównaj poddopasowanie względem sekwencji.|
|[Długość](#length)|Zwraca długość poddopasowanie.|
|[dopasowane](#matched)|Wskazuje, czy dopasowanie zakończyła się pomyślnie.|
|[str](#str)|Konwertuje poddopasowanie na ciąg.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[Operator basic_string < value_type >](#op_basic_string_lt_value_type_gt)|Poddopasowanie rzutowania na ciąg.|

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

**Nagłówek:** \<wyrażenia regularnego >

**Namespace:** standardowe

## <a name="compare"></a>  sub_match::COMPARE

Porównaj poddopasowanie względem sekwencji.

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parametry

*right*  
 Poddopasowanie do porównania.

*str*  
 Ciąg do porównania.

*ptr*  
 Sekwencja zakończony wartością null do porównania.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego porównuje dopasowane sekwencji `[first, second)` dopasowane sekwencji `[right.first, right.second)`. Funkcja drugiego członka porównuje dopasowane sekwencji `[first, second)` sekwencję znaków `[right.begin(), right.end())`. Trzecia funkcja członkowska porównuje dopasowane sekwencji `[first, second)` sekwencję znaków `[right, right + std::char_traits<value_type>::length(right))`.

Każda funkcja zwraca:

wartość ujemną, jeśli pierwsza wartość różne dopasowane sekwencji porównuje mniej niż odpowiadający mu element w sekwencji operand (zgodnie z ustaleniami `std::char_traits<value_type>::compare`), czy dwa mają Wspólny prefiks, ale nie do sekwencji docelowej

zero, jeśli dwa porównywane elementów i tę samą długość

w przeciwnym razie wartość dodatnią

## <a name="difference_type"></a>  sub_match::difference_type

Typ różnicy iteratora.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem dla `iterator_traits<BidIt>::difference_type`.

## <a name="iterator"></a>  sub_match::iterator

Typ iteratora.

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem dla argument typu szablonu `Bidit`.

## <a name="length"></a>  sub_match::length

Zwraca długość poddopasowanie.

```cpp
difference_type length() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca długość dopasowane sekwencji lub zero, jeśli nie było żadnych dopasowane sekwencji.

## <a name="matched"></a>  sub_match::matched

Wskazuje, czy dopasowanie zakończyła się pomyślnie.

```cpp
bool matched;
```

### <a name="remarks"></a>Uwagi

Element członkowski przechowuje **true** tylko wtedy, gdy skojarzona z grupą przechwytywania `*this` było częścią dopasowanie wyrażenia regularnego.

## <a name="op_basic_string_lt_value_type_gt"></a>  sub_match::operator basic_string&lt;value_type&gt;

Poddopasowanie rzutowania na ciąg.

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `str()`.

## <a name="str"></a>  sub_match::str

Konwertuje poddopasowanie na ciąg.

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `basic_string<value_type>(first, second)`.

## <a name="value_type"></a>  sub_match::value_type

Typ elementu.

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem dla `iterator_traits<BidIt>::value_type`.

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)<br/>
[sub_match](../standard-library/sub-match-class.md)<br/>

---
title: '&lt;funkcje wyrażenia regularnego &gt;'
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_match
- regex/std::regex_replace
- regex/std::regex_search
- regex/std::swap
ms.assetid: 91a8314b-6f7c-4e33-b7d6-d8583dd75585
helpviewer_keywords:
- std::regex_match [C++]
- std::regex_replace [C++]
- std::regex_search [C++]
- std::swap [C++]
- std::swap [C++]
ms.openlocfilehash: fd7087025939a0aacf17153f201e37fc377653f9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842874"
---
# <a name="ltregexgt-functions"></a>&lt;funkcje wyrażenia regularnego &gt;

|Nazwa|Opis|
|-|-|
|[regex_match](#regex_match)|Testuje, czy wyrażenie regularne dopasowuje cały ciąg docelowy.|
|[regex_replace](#regex_replace)|Zastępuje dopasowane wyrażenia regularne.|
|[regex_search](#regex_search)|Wyszukuje dopasowanie wyrażenia regularnego.|
|[wymiany](#swap)|Zamienia dwa `basic_regex` lub `match_results` obiekty.|

## <a name="regex_match"></a><a name="regex_match"></a> regex_match

Testuje, czy wyrażenie regularne dopasowuje cały ciąg docelowy.

```cpp
// (1)
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (2)
template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (3)
template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (4)
template <class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (5)
template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (6)
template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>Parametry

*BidIt*\
Typ iteratora dla podpasowań. W przypadku typowych przypadków ten jeden `string::const_iterator` z `wstring::const_iterator` , `const char*` lub `const wchar_t*` .

*Alokacj*\
Klasa alokatora wyników dopasowania.

*Elem*\
Typ elementów, do których ma pasować. W przypadku typowych przypadków jest to, `string` `wstring` `char*` lub `wchar_t*` .

*RXtraits*\
Klasa cech dla elementów.

*Alloc2*\
Klasa alokatora wyrażeń regularnych.

*IOtraits*\
Klasa cech ciągu.

*IOalloc*\
Klasa alokatora ciągów.

*znaczników*\
Flagi dla dopasowania.

*pierwszego*\
Początek sekwencji do dopasowania.

*ostatniego*\
Koniec sekwencji do dopasowania.

*spełnić*\
Wyniki dopasowania. Odnosi się do typu Elem: [Smatch —](../standard-library/regex-typedefs.md#smatch) for `string` , [wsmatch —](../standard-library/regex-typedefs.md#wsmatch) dla `wstring` , [cmatch —](../standard-library/regex-typedefs.md#cmatch) `char*` lub [wcmatch —](../standard-library/regex-typedefs.md#wcmatch) dla `wchar_t*` .

*PTR*\
Wskaźnik na początek sekwencji do dopasowania. Jeśli *PTR* to `char*` , użyj `cmatch` i `regex` . Jeśli *PTR* jest `wchar_t*` następnie używany `wcmatch` i `wregex` .

*Eksport*\
Wyrażenie regularne do dopasowania. Wpisz `regex` dla `string` i `char*` , lub `wregex` dla `wstring` i `wchar_t*` .

*str*\
Ciąg do dopasowania. Odnosi się do typu *elem*.

### <a name="remarks"></a>Uwagi

Każda funkcja szablonu zwraca wartość true tylko wtedy, gdy cały *operand sekwencji jest* dokładnie zgodny *z argumentem*wyrażenia regularnego. Użyj [regex_search](../standard-library/regex-functions.md#regex_search) , aby dopasować podciąg w sekwencji docelowej i `regex_iterator` znaleźć wiele dopasowań. Funkcje, które przyjmują `match_results` obiekt ustawia jego elementy członkowskie, aby odzwierciedlały, czy dopasowanie zakończyło się pomyślnie, a jeśli tak, to jakie są różne grupy przechwytywania w przechwyconym wyrażeniu regularnym.

Funkcje, które przyjmują `match_results` obiekt ustawia jego elementy członkowskie, aby odzwierciedlały, czy dopasowanie zakończyło się pomyślnie, a jeśli tak, to jakie są różne grupy przechwytywania w przechwyconym wyrażeniu regularnym.

### <a name="example"></a>Przykład

```cpp
// std__regex__regex_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    // (1) with char*
    // Note how const char* requires cmatch and regex
    const char *first = "abc";
    const char *last = first + strlen(first);
    cmatch narrowMatch;
    regex rx("a(b)c");

    bool found = regex_match(first, last, narrowMatch, rx);
    if (found)
        wcout << L"Regex found in abc" << endl;

    // (2) with std::wstring
    // Note how wstring requires wsmatch and wregex.
    // Note use of const iterators cbegin() and cend().
    wstring target(L"Hello");
    wsmatch wideMatch;
    wregex wrx(L"He(l+)o");

    if (regex_match(target.cbegin(), target.cend(), wideMatch, wrx))
        wcout << L"The matching text is:" << wideMatch.str() << endl;

    // (3) with std::string
    string target2("Drizzle");
    regex rx2(R"(D\w+e)"); // no double backslashes with raw string literal

    found = regex_match(target2.cbegin(), target2.cend(), rx2);
    if (found)
        wcout << L"Regex found in Drizzle" << endl;

    // (4) with wchar_t*
    const wchar_t* target3 = L"2014-04-02";
    wcmatch wideMatch2;

    // LR"(...)" is a  raw wide-string literal. Open and close parens
    // are delimiters, not string elements.
    wregex wrx2(LR"(\d{4}(-|/)\d{2}(-|/)\d{2})");
    if (regex_match(target3, wideMatch2, wrx2))
    {
        wcout << L"Matching text: " << wideMatch2.str() << endl;
    }

     return 0;
}
```

```Output
Regex found in abc
The matching text is: Hello
Regex found in Drizzle
The matching text is: 2014-04-02
```

## <a name="regex_replace"></a><a name="regex_replace"></a> regex_replace

Zastępuje dopasowane wyrażenia regularne.

```cpp
template <class OutIt, class BidIt, class RXtraits, class Alloc, class Elem>
OutIt regex_replace(
    OutIt out,
    BidIt first,
    BidIt last,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);

template <class RXtraits, class Alloc, class Elem>
basic_string<Elem> regex_replace(
    const basic_string<Elem>& str,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>Parametry

*OutIt*\
Typ iteratora dla zamian.

*BidIt*\
Typ iteratora dla podpasowań.

*RXtraits*\
Klasa cech dla elementów.

*Alokacj*\
Klasa alokatora wyrażeń regularnych.

*Elem*\
Typ elementów, do których ma pasować.

*znaczników*\
Flagi dla dopasowania.

*pierwszego*\
Początek sekwencji do dopasowania.

*FMT*\
Format zamian.

*ostatniego*\
Koniec sekwencji do dopasowania.

*określoną*\
Iterator danych wyjściowych.

*Eksport*\
Wyrażenie regularne do dopasowania.

*str*\
Ciąg do dopasowania.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja konstruuje obiekt [klasy regex_iterator](../standard-library/regex-iterator-class.md) `iter(first, last, re, flags)` i używa jej do podzielenia zakresu wejściowego na `[first, last)` serię podsekwencji `T0 M0 T1 M1...TN-1 MN-1 TN` , gdzie `Mn` to n-ty dopasowanie wykryte przez iterator. Jeśli nie znaleziono żadnych dopasowań, `T0` to cały zakres wejściowy i `N` wynosi zero. Jeśli `(flags & format_first_only) != 0` używane jest tylko pierwsze dopasowanie, `T1` to cały tekst wejściowy, który następuje po dopasowaniu i `N` ma wartość 1. Dla każdego `i` z zakresu `[0, N)` , jeśli `(flags & format_no_copy) == 0` kopiuje tekst z zakresu `Ti` do iteratora. *out* Następnie wywołuje `m.format(out, fmt, flags)` , gdzie `m` jest `match_results` obiektem zwracanym przez obiekt iteratora `iter` dla sekwencji `Mi` . Na koniec, jeśli `(flags & format_no_copy) == 0` kopiuje tekst z zakresu `TN` do iteratora. *out* Funkcja zwraca wartość *out*.

Druga funkcja konstruuje lokalną zmienną `result` typu `basic_string<charT>` i wywołań `regex_replace(back_inserter(result), str.begin(), str.end(), re, fmt, flags)` . Zwraca wartość `result` .

### <a name="example"></a>Przykład

```cpp
// std__regex__regex_replace.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    char buf[20];
    const char *first = "axayaz";
    const char *last = first + strlen(first);
    std::regex rx("a");
    std::string fmt("A");
    std::regex_constants::match_flag_type fonly =
        std::regex_constants::format_first_only;

    *std::regex_replace(&buf[0], first, last, rx, fmt) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    *std::regex_replace(&buf[0], first, last, rx, fmt, fonly) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    std::string str("adaeaf");
    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt) << std::endl;

    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt, fonly) << std::endl;

    return (0);
}
```

```Output
replacement == AxAyAz
replacement == Axayaz
replacement == AdAeAf
replacement == Adaeaf
```

## <a name="regex_search"></a><a name="regex_search"></a> regex_search

Wyszukuje dopasowanie wyrażenia regularnego.

```cpp
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>Parametry

*BidIt*\
Typ iteratora dla podpasowań.

*Alokacj*\
Klasa alokatora wyników dopasowania.

*Elem*\
Typ elementów, do których ma pasować.

*RXtraits*\
Klasa cech dla elementów.

*Alloc2*\
Klasa alokatora wyrażeń regularnych.

*IOtraits*\
Klasa cech ciągu.

*IOalloc*\
Klasa alokatora ciągów.

*znaczników*\
Flagi dla dopasowania.

*pierwszego*\
Początek sekwencji do dopasowania.

*ostatniego*\
Koniec sekwencji do dopasowania.

*spełnić*\
Wyniki dopasowania.

*PTR*\
Wskaźnik na początek sekwencji do dopasowania.

*Eksport*\
Wyrażenie regularne do dopasowania.

*str*\
Ciąg do dopasowania.

### <a name="remarks"></a>Uwagi

Każda funkcja szablonu zwraca wartość true tylko wtedy, gdy wyszukiwanie *jego argumentu* regularnego zostanie wykonane pomyślnie. Funkcje, które przyjmują `match_results` obiekt, w celu określenia, czy wyszukiwanie zakończyło się pomyślnie, a jeśli tak, to jakie są różne grupy przechwytywania w przechwyconym wyrażeniu regularnym.

### <a name="example"></a>Przykład

```cpp
// std__regex__regex_search.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    const char *first = "abcd";
    const char *last = first + strlen(first);
    std::cmatch mr;
    std::regex rx("abc");
    std::regex_constants::match_flag_type fl =
        std::regex_constants::match_default;

    std::cout << "search(f, f+1, \"abc\") == " << std::boolalpha
        << regex_search(first, first + 1, rx, fl) << std::endl;

    std::cout << "search(f, l, \"abc\") == " << std::boolalpha
        << regex_search(first, last, mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(\"a\", \"abc\") == " << std::boolalpha
        << regex_search("a", rx) << std::endl;

    std::cout << "search(\"xabcd\", \"abc\") == " << std::boolalpha
        << regex_search("xabcd", mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(std::string("a"), rx) << std::endl;

    std::string str("abcabc");
    std::match_results<std::string::const_iterator> mr2;
    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(str, mr2, rx) << std::endl;
    std::cout << "  matched: \"" << mr2.str() << "\"" << std::endl;

    return (0);
}
```

```Output
search(f, f+1, "abc") == false
search(f, l, "abc") == true
  matched: "abc"
search("a", "abc") == false
search("xabcd", "abc") == true
  matched: "abc"
search(string, "abc") == false
search(string, "abc") == true
  matched: "abc"
```

## <a name="swap"></a><a name="swap"></a> wymiany

Zamienia dwa `basic_regex` lub `match_results` obiekty.

```cpp
template <class Elem, class RXtraits>
void swap(
    basic_regex<Elem, RXtraits, Alloc>& left,
    basic_regex<Elem, RXtraits>& right) noexcept;

template <class Elem, class IOtraits, class BidIt, class Alloc>
void swap(
    match_results<BidIt, Alloc>& left,
    match_results<BidIt, Alloc>& right) noexcept;
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ elementów, do których ma pasować.

*RXtraits*\
Klasa cech dla elementów.

### <a name="remarks"></a>Uwagi

Funkcje szablonu zamieniają zawartość odpowiednich argumentów w stałym czasie i nie generują wyjątków.

### <a name="example"></a>Przykład

```cpp
// std__regex__swap.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx0("c(a*)|(b)");
    std::regex rx1;
    std::cmatch mr0;
    std::cmatch mr1;

    swap(rx0, rx1);
    std::regex_search("xcaaay", mr1, rx1);
    swap(mr0, mr1);

    std::csub_match sub = mr0[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;
    std::cout << "string == " << sub << std::endl;

    return (0);
}
```

```Output
matched == true
length == 3
string == aaa
```

## <a name="see-also"></a>Zobacz też

[\<regex>](../standard-library/regex.md)\
[Klasa regex_constants](../standard-library/regex-constants-class.md)\
[Klasa regex_error](../standard-library/regex-error-class.md)\
[Klasa regex_iterator](../standard-library/regex-iterator-class.md)\
[\<regex> zainteresowanych](../standard-library/regex-operators.md)\
[Klasa regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Klasa regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> definicje typów](../standard-library/regex-typedefs.md)

---
title: '&lt;wyrażenie regularne&gt; funkcji'
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
ms.openlocfilehash: 47b3ae9d59db7c39d7b9667038d216f24530d5dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62369608"
---
# <a name="ltregexgt-functions"></a>&lt;wyrażenie regularne&gt; funkcji

|||
|-|-|
|[regex_match](#regex_match)|Sprawdza, czy wyrażenie regularne pasuje do ciągu w całej docelowej.|
|[regex_replace](#regex_replace)|Zamienia dopasowany wyrażeń regularnych.|
|[regex_search](#regex_search)|Wyszukuje dopasowania wyrażenia regularnego.|
|[swap](#swap)|Zamień dwa `basic_regex` lub `match_results` obiektów.|

## <a name="regex_match"></a>  regex_match —

Sprawdza, czy wyrażenie regularne pasuje do ciągu w całej docelowej.

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

*BidIt*<br/>
Typ iteratora poddopasowania. Dla typowych przypadków to `string::const_iterator`, `wstring::const_iterator`, `const char*` lub `const wchar_t*`.

*Alokacji*<br/>
Klasa alokatora wyników dopasowania.

*Elem*<br/>
Typ elementów, do których ma pasować. Dla typowych przypadków `string`, `wstring`, `char*` lub `wchar_t*`.

*RXtraits*<br/>
Klasa cech dla elementów.

*Alloc2*<br/>
Klasa alokatora wyrażenia regularnego.

*IOtraits*<br/>
Klasa cech ciągu.

*IOalloc*<br/>
Klasa alokatora ciągu.

*flagi*<br/>
Flagi dopasowania.

*pierwszy*<br/>
Początek sekwencji w celu dopasowania.

*last*<br/>
Koniec sekwencji w celu dopasowania.

*match*<br/>
Wyniki dopasowania. Odnosi się do typu Elem: [smatch](../standard-library/regex-typedefs.md#smatch) dla `string`, [wsmatch](../standard-library/regex-typedefs.md#wsmatch) dla `wstring`, [cmatch](../standard-library/regex-typedefs.md#cmatch) dla `char*` lub [wcmatch](../standard-library/regex-typedefs.md#wcmatch) dla `wchar_t*`.

*ptr*<br/>
Wskaźnik do początku sekwencji do dopasowania. Jeśli *ptr* jest `char*`, następnie za pomocą `cmatch` i `regex`. Jeśli *ptr* jest `wchar_t*` następnie za pomocą `wcmatch` i `wregex`.

*środowisko odzyskiwania*<br/>
Wyrażenie regularne do dopasowania. Typ `regex` dla `string` i `char*`, lub `wregex` dla `wstring` i `wchar_t*`.

*str*<br/>
Ciąg do dopasowania. Odnosi się do typu *Elem*.

### <a name="remarks"></a>Uwagi

Każda funkcja szablonu zwraca wartość PRAWDA, tylko wtedy, gdy sekwencję operandów całego *str* dokładnie odpowiada argument wyrażenia regularnego *re*. Użyj [regex_search —](../standard-library/regex-functions.md#regex_search) do dopasowania podciągu w sekwencji docelowej i `regex_iterator` można znaleźć wiele dopasowań. Funkcje, których `match_results` obiektu ustaw jego członków w celu odzwierciedlenia czy dopasowanie zakończyło się pomyślnie, a jeśli tak, co różne grupy przechwytywania w wyrażeniu regularnym przechwytywane.

Funkcje, których `match_results` obiektu ustaw jego członków w celu odzwierciedlenia czy dopasowanie zakończyło się pomyślnie, a jeśli tak, co różne grupy przechwytywania w wyrażeniu regularnym przechwytywane.

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

## <a name="regex_replace"></a>  regex_replace —

Zamienia dopasowany wyrażeń regularnych.

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

*OutIt*<br/>
Typ iteratora do zamiany.

*BidIt*<br/>
Typ iteratora poddopasowania.

*RXtraits*<br/>
Klasa cech dla elementów.

*Alokacji*<br/>
Klasa alokatora wyrażenia regularnego.

*Elem*<br/>
Typ elementów, do których ma pasować.

*flagi*<br/>
Flagi dopasowania.

*pierwszy*<br/>
Początek sekwencji w celu dopasowania.

*fmt*<br/>
Format zamiany.

*last*<br/>
Koniec sekwencji w celu dopasowania.

*out*<br/>
Iterator danych wyjściowych.

*środowisko odzyskiwania*<br/>
Wyrażenie regularne do dopasowania.

*str*<br/>
Ciąg do dopasowania.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja tworzy [regex_iterator, klasa](../standard-library/regex-iterator-class.md) obiektu `iter(first, last, re, flags)` i używa go do dzielenia jej zakresu wejściowego `[first, last)` do kilku podciągów `T0 M0 T1 M1...TN-1 MN-1 TN`, gdzie `Mn` n-match zostanie wykryty przez Iterator. W przypadku nieodnalezienia żadnych dopasowań `T0` jest cały zakres danych wejściowych i `N` wynosi zero. Jeśli `(flags & format_first_only) != 0` służy tylko pierwsze dopasowanie, `T1` to wszystko wprowadzany tekst, który następuje po dopasowaniu i `N` 1. Dla każdego `i` w zakresie `[0, N)`, jeśli `(flags & format_no_copy) == 0` kopiuje tekst w zakresie `Ti` do iteratora *się*. Następnie wywołuje `m.format(out, fmt, flags)`, gdzie `m` jest `match_results` obiektu zwróconego przez obiekt iteratora `iter` dla podsekwencją `Mi`. Ponadto jeśli `(flags & format_no_copy) == 0` kopiuje tekst w zakresie `TN` do iteratora *się*. Funkcja zwraca *się*.

Druga funkcja tworzy zmienną lokalną `result` typu `basic_string<charT>` i wywołania `regex_replace(back_inserter(result), str.begin(), str.end(), re, fmt, flags)`. Zwraca `result`.

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

## <a name="regex_search"></a>  regex_search —

Wyszukuje dopasowania wyrażenia regularnego.

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

*BidIt*<br/>
Typ iteratora poddopasowania.

*Alokacji*<br/>
Klasa alokatora wyników dopasowania.

*Elem*<br/>
Typ elementów, do których ma pasować.

*RXtraits*<br/>
Klasa cech dla elementów.

*Alloc2*<br/>
Klasa alokatora wyrażenia regularnego.

*IOtraits*<br/>
Klasa cech ciągu.

*IOalloc*<br/>
Klasa alokatora ciągu.

*flagi*<br/>
Flagi dopasowania.

*pierwszy*<br/>
Początek sekwencji w celu dopasowania.

*last*<br/>
Koniec sekwencji w celu dopasowania.

*match*<br/>
Wyniki dopasowania.

*ptr*<br/>
Wskaźnik do początku sekwencji do dopasowania.

*środowisko odzyskiwania*<br/>
Wyrażenie regularne do dopasowania.

*str*<br/>
Ciąg do dopasowania.

### <a name="remarks"></a>Uwagi

Każda funkcja szablonu zwraca wartość true tylko wtedy, gdy wyszukiwanie jej argument wyrażenia regularnego *re* w swojego operandu sekwencji powiedzie się. Funkcje, których `match_results` obiektu ustaw jego członków w celu odzwierciedlenia czy wyszukiwanie zakończyło się pomyślnie, a jeśli tak, co różne grupy przechwytywania w wyrażeniu regularnym przechwytywane.

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

## <a name="swap"></a>  swap

Zamień dwa `basic_regex` lub `match_results` obiektów.

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

*Elem*<br/>
Typ elementów, do których ma pasować.

*RXtraits*<br/>
Klasa cech dla elementów.

### <a name="remarks"></a>Uwagi

Funkcje szablonu wymiany zawartość ich odpowiednich argumentów w stałym czasie i nie zgłasza wyjątków.

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

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants, klasa](../standard-library/regex-constants-class.md)<br/>
[regex_error, klasa](../standard-library/regex-error-class.md)<br/>
[regex_iterator, klasa](../standard-library/regex-iterator-class.md)<br/>
[\<wyrażenie regularne > operatorów](../standard-library/regex-operators.md)<br/>
[regex_token_iterator, klasa](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits, klasa](../standard-library/regex-traits-class.md)<br/>
[\<wyrażenie regularne > definicje typów](../standard-library/regex-typedefs.md)<br/>

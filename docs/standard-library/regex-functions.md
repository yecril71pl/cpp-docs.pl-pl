---
title: '&lt;wyrażenie regularne&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/19/2018
ms.topic: reference
f1_keywords:
- regex/std::regex_match
- regex/std::regex_replace
- regex/std::regex_search
- regex/std::swap
dev_langs:
- C++
ms.assetid: 91a8314b-6f7c-4e33-b7d6-d8583dd75585
helpviewer_keywords:
- std::regex_match [C++]
- std::regex_replace [C++]
- std::regex_search [C++]
- std::swap [C++]
- std::swap [C++]
ms.openlocfilehash: 0bc0fc88c3bdd370222e80f6ab96f33d5dd7df28
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305647"
---
# <a name="ltregexgt-functions"></a>&lt;wyrażenie regularne&gt; funkcji

||||
|-|-|-|
|[regex_match](#regex_match)|[regex_replace](#regex_replace)|[regex_search](#regex_search)|
|[swap](#swap)|

## <a name="regex_match"></a>  regex_match —

Sprawdza, czy wyrażenie regularne dopasowuje ciąg całego docelowego.

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

|||
|-|-|
*BidIt*| Typ iteratora submatches. Dla typowe przypadki to jeden z `string::const_iterator`, `wstring::const_iterator`, `const char*` lub `const wchar_t*`.
*Alokacji*| Klasa alokatora wyniki dopasowania.
*Element*| Typ elementów, do których ma pasować. Typowe przypadków jest `string`, `wstring`, `char*` lub `wchar_t*`.
*RXtraits*| Klasa cech dla elementów.
*Alloc2*| Allocator — klasa wyrażenia regularnego.
*IOtraits*| Klasa cech ciągu.
*IOalloc*| Allocator — klasa ciągu.
*Flagi*| Flagi do dopasowania.
*pierwszy*| Początek sekwencji do dopasowania.
*ostatni*| Koniec sekwencji do dopasowania.
*match*| Wyniki zgodne. Odnosi się do typu elementu: [smatch](../standard-library/regex-typedefs.md#smatch) dla `string`, [wsmatch](../standard-library/regex-typedefs.md#wsmatch) dla `wstring`, [cmatch](../standard-library/regex-typedefs.md#cmatch) dla `char*` lub [wcmatch](../standard-library/regex-typedefs.md#wcmatch) dla `wchar_t*`.
*ptr*| Wskaźnik do początku sekwencji do dopasowania. Jeśli *ptr* jest `char*`, następnie użyć `cmatch` i `regex`. Jeśli *ptr* jest `wchar_t*` następnie użyć `wcmatch` i `wregex`.
*Ponowna*| Wyrażenie regularne do dopasowania. Typ `regex` dla `string` i `char*`, lub `wregex` dla `wstring` i `wchar_t*`.
*str*| Ciąg do dopasowania. Odnosi się do typu *elementu*.

### <a name="remarks"></a>Uwagi

Funkcja każdego szablonu zwraca wartość PRAWDA tylko wtedy, gdy sekwencja cały operand *str* dokładnie odpowiada argument wyrażenia regularnego *re*. Użyj [regex_search —](../standard-library/regex-functions.md#regex_search) odpowiadające substring w sekwencji docelowych i `regex_iterator` można znaleźć wiele dopasowań. Funkcje, których `match_results` jej elementów członkowskich w celu odzwierciedlenia czy dopasowania zakończyło się pomyślnie, a jeśli tak, co przechwytywania różnych grup w wyrażeniu regularnym przechwycone ustawienie obiektu.

Funkcje, których `match_results` jej elementów członkowskich w celu odzwierciedlenia czy dopasowania zakończyło się pomyślnie, a jeśli tak, co przechwytywania różnych grup w wyrażeniu regularnym przechwycone ustawienie obiektu.

### <a name="example"></a>Przykład

```cpp
#include "stdafx.h"
#include <regex>
#include <iostream>

using namespace std;

int _tmain(int argc, _TCHAR* argv[])
{

    // (1) with char*
    // Note how const char* requires cmatch and regex
    const char *first = "abc";
    const char *last = first + strlen(first);
    cmatch narrowMatch;
    regex rx("a(b)c");

    bool found = regex_match(first, last, narrowMatch, rx);

    // (1) with std::wstring
    // Note how wstring requires wsmatch and wregex.
    // Note use of const iterators cbegin() and cend().
    wstring target(L"Hello");
    wsmatch wideMatch;
    wregex wrx(L"He(l+)o");

    if (regex_match(target.cbegin(), target.cend(), wideMatch, wrx))
        wcout << L"The matching text is:" << wideMatch.str() << endl;

    // (2) with std::string
    string target2("Drizzle");
    regex rx2(R"(D\w+e)"); // no double backslashes with raw string literal
    found = regex_match(target2.cbegin(), target2.cend(), rx2);

    // (3) with wchar_t*
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

## <a name="regex_replace"></a>  regex_replace —

Zamienia dopasowaniu wyrażenia regularne.

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

|||
|-|-|
*OutIt*| Typ iteratora zamiany.
*BidIt*| Typ iteratora submatches.
*RXtraits*| Klasa cech dla elementów.
*Alokacji*| Allocator — klasa wyrażenia regularnego.
*Element*| Typ elementów, do których ma pasować.
*Flagi*| Flagi do dopasowania.
*pierwszy*| Początek sekwencji do dopasowania.
*formatowaniu*| Format wymiany.
*ostatni*| Koniec sekwencji do dopasowania.
*out*| Iterator danych wyjściowych.
*Ponowna*| Wyrażenie regularne do dopasowania.
*str*| Ciąg do dopasowania.

### <a name="remarks"></a>Uwagi

Konstruuje pierwszej funkcji [regex_iterator — klasa](../standard-library/regex-iterator-class.md) obiektu `iter(first, last, re, flags)` i używa go do jego zakresu wejściowego podzielić `[first, last)` do serii podciągów `T0 M0 T1 M1...TN-1 MN-1 TN`, gdzie `Mn` n-ty dopasowania wykrywane przez Iterator. W przypadku nieodnalezienia żadnych dopasowań `T0` jest cały zakres wejściowy i `N` wynosi zero. Jeśli `(flags & format_first_only) != 0` służy tylko pierwszego dopasowania, `T1` jest cały tekst wejściowy znajdujący się zgodne, i `N` 1. Dla każdego `i` w zakresie `[0, N)`, jeśli `(flags & format_no_copy) == 0` w zakresie kopiuje tekst `Ti` do iteratora *limit*. Następnie wywołuje `m.format(out, fmt, flags)`, gdzie `m` jest `match_results` obiektów zwrócona przez obiekt iteratora `iter` dla podsekwencji `Mi`. Ponadto jeśli `(flags & format_no_copy) == 0` w zakresie kopiuje tekst `TN` do iteratora *limit*. Funkcja zwraca *limit*.

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

Wyszukuje wyrażenie regularne zgodne.

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

|||
|-|-|
*BidIt*| Typ iteratora submatches.
*Alokacji*| Klasa alokatora wyniki dopasowania.
*Element*| Typ elementów, do których ma pasować.
*RXtraits*| Klasa cech dla elementów.
*Alloc2*| Allocator — klasa wyrażenia regularnego.
*IOtraits*| Klasa cech ciągu.
*IOalloc*| Allocator — klasa ciągu.
*Flagi*| Flagi do dopasowania.
*pierwszy*| Początek sekwencji do dopasowania.
*ostatni*| Koniec sekwencji do dopasowania.
*match*| Wyniki zgodne.
*ptr*| Wskaźnik do początku sekwencji do dopasowania.
*Ponowna*| Wyrażenie regularne do dopasowania.
*str*| Ciąg do dopasowania.

### <a name="remarks"></a>Uwagi

Każdy szablon funkcja zwraca wartość true, tylko wtedy, gdy wyszukiwanie jej argument wyrażenia regularnego *re* w jej argument operacji sekwencji powiedzie się. Funkcje, których `match_results` obiektu ustawić jej elementów członkowskich w celu odzwierciedlenia czy wyszukiwanie zakończyło się pomyślnie, a jeśli tak, co przechwytywania różnych grup w wyrażeniu regularnym przechwytywane.

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

## <a name="swap"></a>  Swap

Zamienia dwa `basic_regex` lub `match_results` obiektów.

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

|||
|-|-|
*Element*| Typ elementów, do których ma pasować.
*RXtraits*| Klasa cech dla elementów.

### <a name="remarks"></a>Uwagi

Funkcje szablonów zamiana zawartość ich odpowiednich argumentów w czasie stała i nie zgłaszają wyjątki.

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

- [\<regex>](../standard-library/regex.md)
- [regex_constants, klasa](../standard-library/regex-constants-class.md)
- [regex_error, klasa](../standard-library/regex-error-class.md)
- [regex_iterator, klasa](../standard-library/regex-iterator-class.md)
- [\<wyrażenie regularne > operatory](../standard-library/regex-operators.md)
- [regex_token_iterator, klasa](../standard-library/regex-token-iterator-class.md)
- [regex_traits, klasa](../standard-library/regex-traits-class.md)
- [\<wyrażenie regularne > definicje typów](../standard-library/regex-typedefs.md)

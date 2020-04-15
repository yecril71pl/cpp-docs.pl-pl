---
title: '&lt;funkcje&gt; regex'
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
ms.openlocfilehash: ff6ea37208aef19431bf7aefe612dccd589c638b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374540"
---
# <a name="ltregexgt-functions"></a>&lt;funkcje&gt; regex

|||
|-|-|
|[regex_match](#regex_match)|Sprawdza, czy wyrażenie regularne pasuje do całego ciągu docelowego.|
|[regex_replace](#regex_replace)|Zastępuje dopasowane wyrażenia regularne.|
|[regex_search](#regex_search)|Wyszukuje dopasowanie wyrażenia regularnego.|
|[Wymiany](#swap)|Zamienia dwa `basic_regex` `match_results` lub obiekty.|

## <a name="regex_match"></a><a name="regex_match"></a>regex_match

Sprawdza, czy wyrażenie regularne pasuje do całego ciągu docelowego.

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

*OfertaIt*\
Typ iteratora dla podmeczów. W typowych przypadkach `string::const_iterator` `wstring::const_iterator`jest `const char*` `const wchar_t*`to jeden z , lub .

*Alloc*\
Klasa alokatora wyników meczu.

*Elem*\
Typ elementów, do których ma pasować. W przypadku typowych `wstring` `char*` przypadków `wchar_t*`jest `string`to , lub .

*RXtraits ( RXtraits )*\
Klasa cech dla elementów.

*Alloc2 (własnach)*\
Klasa alokatora wyrażeń regularnych.

*IOtraits*\
Klasa cech ciągu.

*Ioalloc (właso)*\
Klasa alokatora ciągów.

*Flagi*\
Flagi dla meczów.

*Pierwszym*\
Początek sekwencji do dopasowania.

*Ostatnio*\
Koniec sekwencji do dopasowania.

*Mecz*\
Wyniki meczu. Odpowiada elem typu: [smatch](../standard-library/regex-typedefs.md#smatch) dla `string`, [wsmatch](../standard-library/regex-typedefs.md#wsmatch) dla `wstring`, [cmatch](../standard-library/regex-typedefs.md#cmatch) dla `char*` lub [wcmatch](../standard-library/regex-typedefs.md#wcmatch) dla `wchar_t*`.

*Ptr*\
Wskaźnik do początku sekwencji, aby dopasować. Jeśli *ptr* jest `char*` `cmatch` , `regex`a następnie użyć i . Jeśli *ptr* `wchar_t*` jest `wcmatch` `wregex`następnie użyć i .

*Ponownie*\
Wyrażenie regularne do dopasowania. Wpisz `regex` `string` i `char*`, `wregex` `wstring` lub `wchar_t*`dla i .

*Str*\
Ciąg do dopasowania. Odpowiada typowi *Elem*.

### <a name="remarks"></a>Uwagi

Każda funkcja szablonu zwraca wartość true tylko wtedy, gdy cała sekwencja *operandu str* dokładnie pasuje do argumentu wyrażenia regularnego *ponownie*. Użyj [regex_search,](../standard-library/regex-functions.md#regex_search) aby dopasować podciąg `regex_iterator` w sekwencji docelowej i znaleźć wiele dopasowań. Funkcje, które `match_results` zajmują obiekt ustawić jego członków, aby odzwierciedlić, czy dopasowanie zakończyło się pomyślnie, a jeśli tak, co różne grupy przechwytywania w wyrażeniu regularnym przechwycone.

Funkcje, które `match_results` zajmują obiekt ustawić jego członków, aby odzwierciedlić, czy dopasowanie zakończyło się pomyślnie, a jeśli tak, co różne grupy przechwytywania w wyrażeniu regularnym przechwycone.

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

## <a name="regex_replace"></a><a name="regex_replace"></a>regex_replace

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

*OutIt (OutIt)*\
Typ iteratora dla zamienników.

*OfertaIt*\
Typ iteratora dla podmeczów.

*RXtraits ( RXtraits )*\
Klasa cech dla elementów.

*Alloc*\
Klasa alokatora wyrażeń regularnych.

*Elem*\
Typ elementów, do których ma pasować.

*Flagi*\
Flagi dla meczów.

*Pierwszym*\
Początek sekwencji do dopasowania.

*Fmt*\
Format zamienników.

*Ostatnio*\
Koniec sekwencji do dopasowania.

*na zewnątrz*\
Iterator wyjściowy.

*Ponownie*\
Wyrażenie regularne do dopasowania.

*Str*\
Ciąg do dopasowania.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja konstruuje obiekt `iter(first, last, re, flags)` [regex_iterator Class](../standard-library/regex-iterator-class.md) i używa go `[first, last)` do podzielenia jego zakresu `T0 M0 T1 M1...TN-1 MN-1 TN`wejściowego `Mn` na serię podsekwencji , gdzie jest n-tym dopasowanie wykryte przez iteratora. Jeśli nie znaleziono `T0` żadnych dopasowań, `N` jest to cały zakres wejściowy i wynosi zero. Jeśli `(flags & format_first_only) != 0` używany jest tylko `T1` pierwszy mecz, jest to cały tekst `N` wejściowy, który następuje po dopasowaniu i jest 1. Dla `i` każdego z `[0, N)`nich `(flags & format_no_copy) == 0` w zakresie , jeśli `Ti` kopiuje tekst w zakresie do iteratora *.* Następnie wywołuje `m.format(out, fmt, flags)`, `m` gdzie `match_results` jest obiekt zwracany `iter` przez obiekt iteratora dla podsekwencji `Mi`. Na koniec, `(flags & format_no_copy) == 0` jeśli kopiuje tekst `TN` w zakresie do iteratora *.* Funkcja *zwraca wartość*.

Druga funkcja tworzy zmienną `result` lokalną `basic_string<charT>` typu `regex_replace(back_inserter(result), str.begin(), str.end(), re, fmt, flags)`i wywołuje . Zwraca `result`.

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

## <a name="regex_search"></a><a name="regex_search"></a>regex_search

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

*OfertaIt*\
Typ iteratora dla podmeczów.

*Alloc*\
Klasa alokatora wyników meczu.

*Elem*\
Typ elementów, do których ma pasować.

*RXtraits ( RXtraits )*\
Klasa cech dla elementów.

*Alloc2 (własnach)*\
Klasa alokatora wyrażeń regularnych.

*IOtraits*\
Klasa cech ciągu.

*Ioalloc (właso)*\
Klasa alokatora ciągów.

*Flagi*\
Flagi dla meczów.

*Pierwszym*\
Początek sekwencji do dopasowania.

*Ostatnio*\
Koniec sekwencji do dopasowania.

*Mecz*\
Wyniki meczu.

*Ptr*\
Wskaźnik do początku sekwencji, aby dopasować.

*Ponownie*\
Wyrażenie regularne do dopasowania.

*Str*\
Ciąg do dopasowania.

### <a name="remarks"></a>Uwagi

Każda funkcja szablonu zwraca wartość true tylko wtedy, gdy wyszukiwanie jego argument wyrażenia regularnego *ponownie* w sekwencji operand powiedzie się. Funkcje, które `match_results` zajmują obiekt ustawić jego członków, aby odzwierciedlić, czy wyszukiwanie zakończyło się pomyślnie, a jeśli tak, co różne grupy przechwytywania w wyrażeniu regularnym przechwycone.

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

## <a name="swap"></a><a name="swap"></a>Wymiany

Zamienia dwa `basic_regex` `match_results` lub obiekty.

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

*RXtraits ( RXtraits )*\
Klasa cech dla elementów.

### <a name="remarks"></a>Uwagi

Funkcje szablonu zamieniają zawartość ich odpowiednich argumentów w stałym czasie i nie zgłaszają wyjątków.

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

[\<>regex](../standard-library/regex.md)\
[Klasa regex_constants](../standard-library/regex-constants-class.md)\
[Klasa regex_error](../standard-library/regex-error-class.md)\
[Klasa regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operatorzy> regex](../standard-library/regex-operators.md)\
[Klasa regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Klasa regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)

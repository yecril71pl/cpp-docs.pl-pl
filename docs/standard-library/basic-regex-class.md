---
title: basic_regex — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::basic_regex
dev_langs:
- C++
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f13dfb45073a1a21e8d6a7b4585f0dfc5c71b8e
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959751"
---
# <a name="basicregex-class"></a>basic_regex — Klasa

Owija wyrażenie regularne.

## <a name="syntax"></a>Składnia

```cpp
class basic_regex {
   public:
   basic_regex();
   explicit basic_regex(const Elem *ptr,
   flag_type flags = ECMAScript);
   basic_regex(const Elem *ptr, size_type len,
   flag_type flags = ECMAScript);
   basic_regex(const basic_regex& right);
   template <class STtraits, class STalloc>
   explicit basic_regex(const basic_string<Elem, STtraits, STalloc>& str,
   flag_type flags = ECMAScript);
   template <class InIt>
   explicit basic_regex(InIt first, InIt last,
   flag_type flags = ECMAScript);
   basic_regex& operator=(const basic_regex& right);
   basic_regex& operator=(const Elem *ptr);
   template <class STtraits, class STalloc>
   basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
   basic_regex& assign(const basic_regex& right);
   basic_regex& assign(const Elem *ptr,
   flag_type flags = ECMAScript);
   basic_regex& assign(const Elem *ptr, size_type len,
   flag_type flags = ECMAScript);
   template <class STtraits, class STalloc>
   basic_regex& assign(const basic_string<Elem, STtraits, STalloc>& str,
   flag_type flags = ECMAScript);
   template <class InIt>
   basic_regex& assign(InIt first, InIt last,
   flag_type flags = ECMAScript);
   locale_type imbue(locale_type loc);
   locale_type getloc() const;
   void swap(basic_regex& other) throw();
   unsigned mark_count() const;
   flag_type flags() const;
   typedef Elem value_type;
   typedef regex_constants::syntax_option_type flag_type;
   typedef typename RXtraits::locale_type locale_type;
   static const flag_type icase = regex_constants::icase;
   static const flag_type nosubs = regex_constants::nosubs;
   static const flag_type optimize = regex_constants::optimize;
   static const flag_type collate = regex_constants::collate;
   static const flag_type ECMAScript = regex_constants::ECMAScript;
   static const flag_type basic = regex_constants::basic;
   static const flag_type extended = regex_constants::extended;
   static const flag_type awk = regex_constants::awk;
   static const flag_type grep = regex_constants::grep;
   static const flag_type egrep = regex_constants::egrep;
   private:
   RXtraits traits;    // exposition only
   };
   ```

### <a name="parameters"></a>Parametry

*Elem* typ elementów do dopasowania.

*RXtraits* klasa cech dla elementów.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który zawiera wyrażenie regularne. Obiekty tej klasy szablonu mogą być przekazywane do funkcji szablonu [regex_match —](../standard-library/regex-functions.md#regex_match), [regex_search —](../standard-library/regex-functions.md#regex_search), i [regex_replace —](../standard-library/regex-functions.md#regex_replace), wraz z odpowiednimi argumentami ciągu tekstu, Aby wyszukać tekst, który odpowiada wyrażeniu regularnemu. Istnieją dwie specjalizacje tej klasy szablonu, z definicjami typu [wyrażenia regularnego](../standard-library/regex-typedefs.md#regex) dla elementów typu **char**, i [wregex](../standard-library/regex-typedefs.md#wregex) dla elementów typu  **wchar_t**.

Argument szablonu *RXtraits* opisuje różne ważne właściwości składni wyrażeń regularnych, które obsługuje klasa szablonu. Klasa, która określa te cechy wyrażeń regularnych musi mieć ten sam interfejs zewnętrzny co obiekt klasy szablonu [regex_traits, klasa](../standard-library/regex-traits-class.md).

Niektóre funkcje przyjmują sekwencję operandów, która definiuje wyrażenie regularne. Można określić taką sekwencję operandów na kilka sposobów:

`ptr` --sekwencję zakończony znakiem null (taka jak ciąg C dla *Elem* typu **char**) począwszy od `ptr` (może nie być wskaźnikiem typu null), gdzie element kończący jest wartością `value_type()` i nie jest częścią sekwencji operandu

`ptr`, `count` — Sekwencja `count` elementów, poczynając od `ptr` (może nie być wskaźnikiem typu null)

`str` — Sekwencja określona przez `basic_string` obiektu `str`

`first`, `last` — sekwencja elementów rozdzielonych iteratorami `first` i `last`, w zakresie `[first, last)`

`right` -- `basic_regex` obiektu `right`

Te funkcje elementów członkowskich również przyjmują argument `flags` , który określa różne opcje dla interpretacji wyrażenia regularnego w uzupełnieniu do opisanych przez *RXtraits* typu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyrażenia regularnego >

**Namespace:** standardowe

## <a name="assign"></a>  basic_regex::ASSIGN

Przypisuje wartość do obiektu expressoin regularne.

```cpp
basic_regex& assign(
    const basic_regex& right);

basic_regex& assign(
    const Elem* ptr,
    flag_type flags = ECMAScript);

basic_regex& assign(
    const Elem* ptr,
    size_type len,
    flag_type flags = ECMAScript);

basic_regex& assign(
    initializer_list<_Elem> IList,
    flag_type flags = regex_constants::ECMAScript);

template <class STtraits, class STalloc>
basic_regex& assign(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags = ECMAScript);

template <class InIt>
basic_regex& assign(
    InIt first, InIt last,
    flag_type flags = ECMAScript);
```

### <a name="parameters"></a>Parametry

*STtraits* klasa cech dla źródła ciągu.

*STalloc* klasę alokatora dla źródła ciągu.

*InIt* typu iteratora zakres źródła danych wejściowych.

*prawy* wyrażenia regularnego źródła do skopiowania.

*PTR* wskaźnik do początku sekwencji do skopiowania.

*flagi* składni flagi opcji można dodać podczas kopiowania.

*LEN/TD >* długości sekwencji do skopiowania.

*str* ciągu do skopiowania.

*pierwszy* początek sekwencji do skopiowania.

*ostatni* koniec sekwencji do skopiowania.

*IList* initializer_list do skopiowania.

### <a name="remarks"></a>Uwagi

Funkcje elementów członkowskich Zastąp wyrażenie regularne w posiadaniu `*this` z wyrażeniem regularnym opisanego przez sekwencję operandów, zwracany jest `*this`.

### <a name="example"></a>Przykład

```cpp
// std__regex__basic_regex_assign.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    regex::value_type elem = 'x';
    regex::flag_type flag = regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

    // constructors
    regex rx0;
    cout << "match(\"abc\", \"\") == " << boolalpha
        << regex_match("abc", rx0) << endl;

    regex rx1("abcd", regex::ECMAScript);
    cout << "match(\"abc\", \"abcd\") == " << boolalpha
        << regex_match("abc", rx1) << endl;

    regex rx2("abcd", 3);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx2) << endl;

    regex rx3(rx2);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx3) << endl;

    string str("abcd");
    regex rx4(str);
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx4) << endl;

    regex rx5(str.begin(), str.end() - 1);
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx5) << endl;
    cout << endl;

    // assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

    // mark_count
    cout << "\"abc\" mark_count == "
        << regex("abc").mark_count() << endl;
    cout << "\"(abc)\" mark_count == "
        << regex("(abc)").mark_count() << endl;

    // locales
    regex::locale_type loc = rx0.imbue(locale());
    cout << "getloc == imbued == " << boolalpha
        << (loc == rx0.getloc()) << endl;

    // initializer_list
    regex rx6({ 'a', 'b', 'c' }, regex::ECMAScript);
    cout << "match(\"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}

```

```Output
match("abc", "") == falsematch("abc", "abcd") == falsematch("abc", "abc") == truematch("abc", "abc") == truematch(string("abcd"), "abc") == falsematch(string("abc"), "abc") == true"abc" mark_count == 0"(abc)" mark_count == 1getloc == imbued == truematch("abc") == true
```

## <a name="basic_regex"></a>  basic_regex::basic_regex

Skonstruuj obiekt będący wyrażeniem regularnym.

```cpp
basic_regex();

explicit basic_regex(
    const Elem* ptr,
    flag_type flags);

explicit basic_regex(
    const Elem* ptr,
    size_type len,
    flag_type flags);

basic_regex(
    const basic_regex& right);

basic_regex(
    initializer_list<Type> IList,
    flag_type flags);

template <class STtraits, class STalloc>
explicit basic_regex(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags);

template <class InIt>
explicit basic_regex(
    InIt first,
    InIt last,
    flag_type flags);
```

### <a name="parameters"></a>Parametry

*STtraits* klasa cech dla źródła ciągu.

*STalloc* klasę alokatora dla źródła ciągu.

*InIt* typu iteratora zakres źródła danych wejściowych.

*prawy* wyrażenia regularnego źródła do skopiowania.

*PTR* wskaźnik do początku sekwencji do skopiowania.

*flagi* składni flagi opcji można dodać podczas kopiowania.

*LEN/TD >* długości sekwencji do skopiowania.

*str* ciągu do skopiowania.

*pierwszy* początek sekwencji do skopiowania.

*ostatni* koniec sekwencji do skopiowania.

*IList* initializer_list do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt zbudowanego domyślnie typu `RXtraits`.

Pierwszy Konstruktor konstruuje pustą `basic_regex` obiektu. Inne konstruktory konstruowania `basic_regex` obiekt, który zawiera wyrażenie regularne opisanego przez sekwencję operandów.

Pusta `basic_regex` obiekt nie jest zgodny z dowolnej sekwencji znaków, gdy przekazywane do [regex_match —](../standard-library/regex-functions.md#regex_match), [regex_search —](../standard-library/regex-functions.md#regex_search), lub [regex_replace —](../standard-library/regex-functions.md#regex_replace).

### <a name="example"></a>Przykład

```cpp
// std__regex__basic_regex_construct.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    regex::value_type elem = 'x';
    regex::flag_type flag = regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

    // constructors
    regex rx0;
    cout << "match(\"abc\", \"\") == " << boolalpha
        << regex_match("abc", rx0) << endl;

    regex rx1("abcd", regex::ECMAScript);
    cout << "match(\"abc\", \"abcd\") == " << boolalpha
        << regex_match("abc", rx1) << endl;

    regex rx2("abcd", 3);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx2) << endl;

    regex rx3(rx2);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx3) << endl;

    string str("abcd");
    regex rx4(str);
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx4) << endl;

    regex rx5(str.begin(), str.end() - 1);
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx5) << endl;
    cout << endl;

    // assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

    // mark_count
    cout << "\"abc\" mark_count == "
        << regex("abc").mark_count() << endl;
    cout << "\"(abc)\" mark_count == "
        << regex("(abc)").mark_count() << endl;

    // locales
    regex::locale_type loc = rx0.imbue(locale());
    cout << "getloc == imbued == " << boolalpha
        << (loc == rx0.getloc()) << endl;

    // initializer_list
    regex rx6{ { 'a', 'b', 'c' } };
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}

```

```Output
match("abc", "") == falsematch("abc", "abcd") == falsematch("abc", "abc") == truematch("abc", "abc") == truematch(string("abcd"), "abc") == falsematch(string("abc"), "abc") == true"abc" mark_count == 0"(abc)" mark_count == 1getloc == imbued == truematch("abc", "abc") == true
```

## <a name="flag_type"></a>  basic_regex::flag_type

Typ składni flagi opcji.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

### <a name="example"></a>Przykład

```cpp
// std__regex__basic_regex_flag_type.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
    }

```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
```

## <a name="flags"></a>  basic_regex::Flags

Zwraca składni flagi opcji.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość `flag_type` argument przekazany do jednej z najbardziej aktualną wywołania [basic_regex::assign](#assign) funkcji składowych lub, jeśli brak takiego wywołania zostały wprowadzone, wartość przekazywana do konstruktora.

### <a name="example"></a>Przykład

```cpp
// std__regex__basic_regex_flags.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
    }

```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
```

## <a name="getloc"></a>  basic_regex::getloc

Zwraca obiekt ustawień regionalnych przechowywanych.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `traits.` [regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`.

### <a name="example"></a>Przykład

```cpp
// std__regex__basic_regex_getloc.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
    }

```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
```

## <a name="imbue"></a>  basic_regex::imbue

Zmienia obiektu przechowywanych ustawień regionalnych.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parametry

*Lokalizacja* obiekt ustawień regionalnych, który ma być przechowywany.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego opróżnia `*this` i zwraca `traits.` [regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`.

### <a name="example"></a>Przykład

```cpp
// std__regex__basic_regex_imbue.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
    }

```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
```

## <a name="locale_type"></a>  basic_regex::locale_type

Typ obiektu przechowywanych ustawień regionalnych.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type).

### <a name="example"></a>Przykład

```cpp
// std__regex__basic_regex_locale_type.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
    }

```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
```

## <a name="mark_count"></a>  basic_regex::mark_count

Zwraca liczbę dopasowane podwyrażenia.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca liczbę grup przechwytywania w wyrażeniu regularnym.

### <a name="example"></a>Przykład

```cpp
// std__regex__basic_regex_mark_count.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
    }

```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
```

## <a name="op_eq"></a>  basic_regex::operator =

Przypisuje wartość do obiektu będącego wyrażeniem regularnym.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Parametry

*STtraits* klasa cech dla źródła ciągu.

*STalloc* klasę alokatora dla źródła ciągu.

*prawy* wyrażenia regularnego źródła do skopiowania.

*str* ciągu do skopiowania.

### <a name="remarks"></a>Uwagi

Operatory każdego Zastąp wyrażenie regularne w posiadaniu `*this` z wyrażeniem regularnym opisanego przez sekwencję operandów, zwracany jest `*this`.

### <a name="example"></a>Przykład

```cpp
// std__regex__basic_regex_operator_as.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
    }

```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
```

## <a name="swap"></a>  basic_regex::swap

Zamienia dwa obiekty wyrażeń regularnych.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Parametry

*prawy* obiektu będącego wyrażeniem regularnym wymiany.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia wyrażeń regularnych między `*this` i *prawo*. Ją w stałym czasie i zgłasza żadnych wyjątków.

### <a name="example"></a>Przykład

```cpp
// std__regex__basic_regex_swap.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
    }

```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
```

## <a name="value_type"></a>  basic_regex::value_type

Typ elementu.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *Elem*.

### <a name="example"></a>Przykład

```cpp
// std__regex__basic_regex_value_type.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex::value_type elem = 'x';
    std::regex::flag_type flag = std::regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

// constructors
    std::regex rx0;
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha
        << regex_match("abc", rx0) << std::endl;

    std::regex rx1("abcd", std::regex::ECMAScript);
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha
        << regex_match("abc", rx1) << std::endl;

    std::regex rx2("abcd", 3);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx2) << std::endl;

    std::regex rx3(rx2);
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha
        << regex_match("abc", rx3) << std::endl;

    std::string str("abcd");
    std::regex rx4(str);
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx4) << std::endl;

    std::regex rx5(str.begin(), str.end() - 1);
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha
        << regex_match("abc", rx5) << std::endl;
    std::cout << std::endl;

// assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", std::regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

// mark_count
    std::cout << "\"abc\" mark_count == "
        << std::regex("abc").mark_count() << std::endl;
    std::cout << "\"(abc)\" mark_count == "
        << std::regex("(abc)").mark_count() << std::endl;

// locales
    std::regex::locale_type loc = rx0.imbue(std::locale());
    std::cout << "getloc == imbued == " << std::boolalpha
        << (loc == rx0.getloc()) << std::endl;

    return (0);
    }

```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
```

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)<br/>
[regex_match](../standard-library/regex-functions.md#regex_match)<br/>
[regex_search](../standard-library/regex-functions.md#regex_search)<br/>
[regex_replace](../standard-library/regex-functions.md#regex_replace)<br/>
[regex](../standard-library/regex-typedefs.md#regex)<br/>
[wregex](../standard-library/regex-typedefs.md#wregex)<br/>
[regex_traits, klasa](../standard-library/regex-traits-class.md)<br/>

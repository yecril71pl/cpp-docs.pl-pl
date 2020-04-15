---
title: regex_traits — Klasa
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_traits
- regex/std::regex_traits::char_type
- regex/std::regex_traits::size_type
- regex/std::regex_traits::string_type
- regex/std::regex_traits::locale_type
- regex/std::regex_traits::char_class_type
- regex/std::regex_traits::length
- regex/std::regex_traits::translate
- regex/std::regex_traits::translate_nocase
- regex/std::regex_traits::transform
- regex/std::regex_traits::transform_primary
- regex/std::regex_traits::lookup_classname
- regex/std::regex_traits::lookup_collatename
- regex/std::regex_traits::isctype
- regex/std::regex_traits::value
- regex/std::regex_traits::imbue
- regex/std::regex_traits::getloc
helpviewer_keywords:
- std::regex_traits [C++]
- std::regex_traits [C++], char_type
- std::regex_traits [C++], size_type
- std::regex_traits [C++], string_type
- std::regex_traits [C++], locale_type
- std::regex_traits [C++], char_class_type
- std::regex_traits [C++], length
- std::regex_traits [C++], translate
- std::regex_traits [C++], translate_nocase
- std::regex_traits [C++], transform
- std::regex_traits [C++], transform_primary
- std::regex_traits [C++], lookup_classname
- std::regex_traits [C++], lookup_collatename
- std::regex_traits [C++], isctype
- std::regex_traits [C++], value
- std::regex_traits [C++], imbue
- std::regex_traits [C++], getloc
ms.assetid: bc5a5eed-32fc-4eb7-913d-71c42e729e81
ms.openlocfilehash: 8879336c48d0fec8a20411abf1c07d570a1575e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366391"
---
# <a name="regex_traits-class"></a>regex_traits — Klasa

Opisuje właściwości elementów do dopasowywania.

## <a name="syntax"></a>Składnia

```cpp
template<class Elem>
class regex_traits
```

## <a name="parameters"></a>Parametry

*Elem*\
Typ elementu znaku do opisania.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje różne cechy wyrażenia regularnego dla typu *Elem*. Szablon klasy [basic_regex Class](../standard-library/basic-regex-class.md) używa tych informacji do manipulowania elementami typu *Elem*.

Każdy `regex_traits` obiekt posiada obiekt `regex_traits::locale` typu, który jest używany przez niektóre z jego funkcji członkowskich. Domyślne ustawienia regionalne to `regex_traits::locale()`kopia pliku . Funkcja `imbue` elementu członkowskiego zastępuje obiekt ustawień regionalnych, a funkcja `getloc` elementu członkowskiego zwraca kopię obiektu ustawień regionalnych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[regex_traits](#regex_traits)|Konstruuje obiekt.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_class_type](#char_class_type)|Typ desygnatorów klasy znaków.|
|[Char_type](#char_type)|Typ elementu.|
|[locale_type](#locale_type)|Typ przechowywanego obiektu ustawień regionalnych.|
|[size_type](#size_type)|Typ długości sekwencji.|
|[string_type](#string_type)|Typ ciągu elementów.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[getlok](#getloc)|Zwraca przechowywany obiekt ustawień regionalnych.|
|[Nasycić](#imbue)|Zmienia przechowywany obiekt ustawień regionalnych.|
|[isctype (typ)](#isctype)|Testy członkostwa w klasie.|
|[Długość](#length)|Zwraca długość sekwencji zakończonej wartością null.|
|[lookup_classname](#lookup_classname)|Mapuje sekwencję do klasy znaków.|
|[lookup_collatename](#lookup_collatename)|Mapuje sekwencję do elementu sortującego.|
|[Przekształcić](#transform)|Konwertuje na równoważną uporządkowaną sekwencję.|
|[transform_primary](#transform_primary)|Konwertuje na równoważną sekwencję uporządkowaną bez caseless.|
|[Przetłumacz](#translate)|Konwertuje na równoważny element dopasowania.|
|[translate_nocase](#translate_nocase)|Konwertuje na równoważny element dopasowania bez case.|
|[value](#value)|Konwertuje element na wartość cyfry.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> regex

**Przestrzeń nazw:** std

## <a name="example"></a>Przykład

```cpp
// std__regex__regex_traits.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_traits<char> Mytr;
int main()
    {
    Mytr tr;

    Mytr::char_type ch = tr.translate('a');
    std::cout << "translate('a') == 'a' == " << std::boolalpha
        << (ch == 'a') << std::endl;

    std::cout << "nocase 'a' == 'A' == " << std::boolalpha
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))
        << std::endl;

    const char *lbegin = "abc";
    const char *lend = lbegin + strlen(lbegin);
    Mytr::size_type size = tr.length(lbegin);
    std::cout << "length(\"abc\") == " << size <<std::endl;

    Mytr::string_type str = tr.transform(lbegin, lend);
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha
        << (str < "abc") << std::endl;

    const char *ubegin = "ABC";
    const char *uend = ubegin + strlen(ubegin);
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha
        << (tr.transform_primary(ubegin, uend) <
            tr.transform_primary(lbegin, lend))
        << std::endl;

    const char *dig = "digit";
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);
    std::cout << "class digit == d == " << std::boolalpha
        << (cl == tr.lookup_classname(dig, dig + 1))
        << std::endl;

    std::cout << "'3' is digit == " <<std::boolalpha
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))
        << std::endl;

    std::cout << "hex C == " << tr.value('C', 16) << std::endl;

// other members
    str = tr.lookup_collatename(dig, dig + 5);

    Mytr::locale_type loc = tr.getloc();
    tr.imbue(loc);

    return (0);
    }
```

```Output
translate('a') == 'a' == true
nocase 'a' == 'A' == true
length("abc") == 3
transform("abc") < "abc" == false
primary "ABC" < "abc" == false
class digit == d == true
'3' is digit == true
hex C == 12
```

## <a name="regex_traitschar_class_type"></a><a name="char_class_type"></a>regex_traits::char_class_type

Typ desygnatorów klasy znaków.

```cpp
typedef T8 char_class_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla nieokreślonego typu, który wyznacza klasy znaków. Wartości tego typu można łączyć za pomocą `|` operatora do oznaczania klas znaków, które są związkiem klas wyznaczonych przez operandy.

## <a name="regex_traitschar_type"></a><a name="char_type"></a>regex_traits::char_type

Typ elementu.

```cpp
typedef Elem char_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem argumentu `Elem`szablonu .

## <a name="regex_traitsgetloc"></a><a name="getloc"></a>regex_traits::getloc

Zwraca przechowywany obiekt ustawień regionalnych.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego `locale` zwraca przechowywany obiekt.

## <a name="regex_traitsimbue"></a><a name="imbue"></a>regex_traits::imbue

Zmienia przechowywany obiekt ustawień regionalnych.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Obiekt ustawień regionalnych do przechowywania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego kopiuje `locale` *loc* do przechowywanego obiektu i `locale` zwraca kopię poprzedniej wartości przechowywanego obiektu.

## <a name="regex_traitsisctype"></a><a name="isctype"></a>regex_traits::isctype

Testy członkostwa w klasie.

```cpp
bool isctype(char_type ch, char_class_type cls) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do przetestowania.

*Cls*\
Klasy do przetestowania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość true tylko wtedy, gdy *znak ch* znajduje się w klasie znaków wyznaczonej przez *cls*.

## <a name="regex_traitslength"></a><a name="length"></a>regex_traits::długość

Zwraca długość sekwencji zakończonej wartością null.

```cpp
static size_type length(const char_type *str);
```

### <a name="parameters"></a>Parametry

*Str*\
Sekwencja zakończona z wartością null.

### <a name="remarks"></a>Uwagi

Funkcja statycznego elementu `std::char_traits<char_type>::length(str)`członkowskiego zwraca .

## <a name="regex_traitslocale_type"></a><a name="locale_type"></a>regex_traits::locale_type

Typ przechowywanego obiektu ustawień regionalnych.

```cpp
typedef T7 locale_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem dla typu, który hermetyzuje ustawienia regionalne. W specjalizacjach `regex_traits<char>` i `regex_traits<wchar_t>` jest `std::locale`synonimem .

## <a name="regex_traitslookup_classname"></a><a name="lookup_classname"></a>regex_traits::lookup_classname

Mapuje sekwencję do klasy znaków.

```cpp
template <class FwdIt>
char_class_type lookup_classname(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Początek sekwencji, aby wyszukać.

*Ostatnio*\
Koniec sekwencji, aby wyszukać.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość, która wyznacza klasę znaków nazwaną przez sekwencję znaków wskazywała jej argumenty. Wartość nie zależy od przypadku znaków w sekwencji.

Specjalizacja `regex_traits<char>` rozpoznaje `"d"` `"s"`nazwy `"w"` `"alnum"`, `"alpha"` `"blank"`, `"cntrl"` `"digit"`, `"graph"` `"lower"`, `"print"` `"punct"`, `"space"` `"upper"`, `"xdigit"`, , , , , , , i , wszystkie bez względu na przypadek.

Specjalizacja `regex_traits<wchar_t>` rozpoznaje `L"d"` `L"s"`nazwy `L"w"` `L"alnum"`, `L"alpha"` `L"blank"`, `L"cntrl"` `L"digit"`, `L"graph"` `L"lower"`, `L"print"` `L"punct"`, `L"space"` `L"upper"`, `L"xdigit"`, , , , , , , i , wszystkie bez względu na przypadek.

## <a name="regex_traitslookup_collatename"></a><a name="lookup_collatename"></a>regex_traits::lookup_collatename

Mapuje sekwencję do elementu sortującego.

```cpp
template <class FwdIt>
string_type lookup_collatename(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Początek sekwencji, aby wyszukać.

*Ostatnio*\
Koniec sekwencji, aby wyszukać.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca obiekt ciągu zawierający element `[first, last)`sortujący odpowiadający sekwencji lub pusty ciąg, jeśli sekwencja nie jest prawidłowym elementem sortującym.

## <a name="regex_traitsregex_traits"></a><a name="regex_traits"></a>regex_traits::regex_traits

Konstruuje obiekt.

```cpp
regex_traits();
```

### <a name="remarks"></a>Uwagi

Konstruktor tworzy obiekt, `locale` którego przechowywany obiekt jest inicjowany do domyślnych ustawień regionalnych.

## <a name="regex_traitssize_type"></a><a name="size_type"></a>regex_traits::size_type

Typ długości sekwencji.

```cpp
typedef T6 size_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem niepodpisanego typu integralnego. W specjalizacjach `regex_traits<char>` i `regex_traits<wchar_t>` jest `std::size_t`synonimem .

Typedef jest synonimem `std::size_t`.

## <a name="regex_traitsstring_type"></a><a name="string_type"></a>regex_traits::string_type

Typ ciągu elementów.

```cpp
typedef basic_string<Elem> string_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem `basic_string<Elem>`.

## <a name="regex_traitstransform"></a><a name="transform"></a>regex_traits::transform

Konwertuje na równoważną uporządkowaną sekwencję.

```cpp
template <class FwdIt>
string_type transform(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Początek sekwencji do przekształcenia.

*Ostatnio*\
Koniec sekwencji do przekształcenia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca ciąg, który generuje przy użyciu reguły transformacji, która zależy od przechowywanego `locale` obiektu. Dla dwóch sekwencji znaków wyznaczonych przez `[first1, last1)` zakresy iteratora `[first2, last2)`i , `transform(first1, last1) < transform(first2, last2)` jeśli `[first1, last1)` sekwencja znaków wyznaczona przez zakres iteratora sortuje przed sekwencją znaków wyznaczoną przez zakres `[first2, last2)`iteratora .

## <a name="regex_traitstransform_primary"></a><a name="transform_primary"></a>regex_traits::transform_primary

Konwertuje na równoważną sekwencję uporządkowaną bez caseless.

```cpp
template <class FwdIt>
string_type transform_primary(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Początek sekwencji do przekształcenia.

*Ostatnio*\
Koniec sekwencji do przekształcenia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca ciąg, który generuje przy użyciu reguły transformacji, która zależy od przechowywanego `locale` obiektu. Dla dwóch sekwencji znaków wyznaczonych przez `[first1, last1)` zakresy iteratora `[first2, last2)`i , `transform_primary(first1, last1) < transform_primary(first2, last2)` jeśli `[first1, last1)` sekwencja znaków wyznaczona przez zakres iteratora sortuje przed sekwencją znaków wyznaczoną przez zakres `[first2, last2)` iteratora bez względu na przypadek lub akcenty.

## <a name="regex_traitstranslate"></a><a name="translate"></a>regex_traits::przetłumaczyć

Konwertuje na równoważny element dopasowania.

```cpp
char_type translate(char_type ch) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do konwersji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca znak, który generuje przy użyciu reguły transformacji, która zależy od przechowywanego `locale` obiektu. Dla `char_type` dwóch `ch1` `ch2`obiektów `translate(ch1) == translate(ch2)` i `ch1` `ch2` , tylko wtedy i powinien dopasować, gdy jeden występuje w definicji wyrażenia regularnego, a drugi występuje w odpowiedniej pozycji w sekwencji docelowej dla dopasowania zależne od ustawień regionalnych.

## <a name="regex_traitstranslate_nocase"></a><a name="translate_nocase"></a>regex_traits::translate_nocase

Konwertuje na równoważny element dopasowania bez case.

```cpp
char_type translate_nocase(char_type ch) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do konwersji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca znak, który generuje przy użyciu reguły transformacji, która zależy od przechowywanego `locale` obiektu. Dla `char_type` dwóch `ch1` `ch2`obiektów `translate_nocase(ch1) == translate_nocase(ch2)` i `ch1` `ch2` , tylko wtedy i powinien dopasować, gdy jeden występuje w definicji wyrażenia regularnego, a drugi występuje w odpowiedniej pozycji w sekwencji docelowej dla dopasowania bez uwzględniania wielkości liter.

## <a name="regex_traitsvalue"></a><a name="value"></a>regex_traits::wartość

Konwertuje element na wartość cyfry.

```cpp
int value(Elem ch, int radix) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Element do konwersji.

*Podstawa*\
Podstawa arytmetyczna do użycia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość reprezentowaną przez znak *ch* w *radix*podstawowej , lub -1, jeśli *ch* nie jest prawidłową cyfrą w *radix*podstawowej . Funkcja zostanie wywołana tylko z argumentem *radix* 8, 10 lub 16.

## <a name="see-also"></a>Zobacz też

[\<>regex](../standard-library/regex.md)\
[Klasa regex_constants](../standard-library/regex-constants-class.md)\
[Klasa regex_error](../standard-library/regex-error-class.md)\
[\<funkcje> regex](../standard-library/regex-functions.md)\
[Klasa regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operatorzy> regex](../standard-library/regex-operators.md)\
[Klasa regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)\
[regex_traits klasa\<> char](../standard-library/regex-traits-char-class.md)\
[regex_traits\<wchar_t klasa>](../standard-library/regex-traits-wchar-t-class.md)

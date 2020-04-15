---
title: regex_constants — Klasa
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_constants
- regex/std::regex_constants::error_collate
- regex/std::regex_constants::error_ctype
- regex/std::regex_constants::error_escape
- regex/std::regex_constants::error_backref
- regex/std::regex_constants::error_brack
- regex/std::regex_constants::error_paren
- regex/std::regex_constants::error_brace
- regex/std::regex_constants::error_badbrace
- regex/std::regex_constants::error_range
- regex/std::regex_constants::error_space
- regex/std::regex_constants::error_badrepeat
- regex/std::regex_constants::error_complexity
- regex/std::regex_constants::error_stack
- regex/std::regex_constants::error_parse
- regex/std::regex_constants::error_syntax
- regex/std::regex_constants::match_default
- regex/std::regex_constants::match_not_bol
- regex/std::regex_constants::match_not_eol
- regex/std::regex_constants::match_not_bow
- regex/std::regex_constants::match_not_eow
- regex/std::regex_constants::match_any
- regex/std::regex_constants::match_not_null
- regex/std::regex_constants::match_continuous
- regex/std::regex_constants::match_prev_avail
- regex/std::regex_constants::format_default
- regex/std::regex_constants::format_sed
- regex/std::regex_constants::format_no_copy
- regex/std::regex_constants::format_first_only
- regex/std::regex_constants::ECMAScript
- regex/std::regex_constants::basic
- regex/std::regex_constants::extended
- regex/std::regex_constants::awk
- regex/std::regex_constants::grep
- regex/std::regex_constants::egrep
- regex/std::regex_constants::icase
- regex/std::regex_constants::nosubs
- regex/std::regex_constants::optimize
- regex/std::regex_constants::collate
helpviewer_keywords:
- std::regex_constants [C++]
- std::regex_constants [C++], error_collate
- std::regex_constants [C++], error_ctype
- std::regex_constants [C++], error_escape
- std::regex_constants [C++], error_backref
- std::regex_constants [C++], error_brack
- std::regex_constants [C++], error_paren
- std::regex_constants [C++], error_brace
- std::regex_constants [C++], error_badbrace
- std::regex_constants [C++], error_range
- std::regex_constants [C++], error_space
- std::regex_constants [C++], error_badrepeat
- std::regex_constants [C++], error_complexity
- std::regex_constants [C++], error_stack
- std::regex_constants [C++], error_parse
- std::regex_constants [C++], error_syntax
- std::regex_constants [C++], match_default
- std::regex_constants [C++], match_not_bol
- std::regex_constants [C++], match_not_eol
- std::regex_constants [C++], match_not_bow
- std::regex_constants [C++], match_not_eow
- std::regex_constants [C++], match_any
- std::regex_constants [C++], match_not_null
- std::regex_constants [C++], match_continuous
- std::regex_constants [C++], match_prev_avail
- std::regex_constants [C++], format_default
- std::regex_constants [C++], format_sed
- std::regex_constants [C++], format_no_copy
- std::regex_constants [C++], format_first_only
- std::regex_constants [C++], ECMAScript
- std::regex_constants [C++], basic
- std::regex_constants [C++], extended
- std::regex_constants [C++], awk
- std::regex_constants [C++], grep
- std::regex_constants [C++], egrep
- std::regex_constants [C++], icase
- std::regex_constants [C++], nosubs
- std::regex_constants [C++], optimize
- std::regex_constants [C++], collate
ms.assetid: 4a69c0ba-c46d-46e4-bd29-6f4efb805f26
ms.openlocfilehash: ee016e5cee1bde94a49a1b339d6910d60db4cea1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331962"
---
# <a name="regex_constants-namespace"></a>regex_constants, przestrzeń nazw

Przestrzeń nazw dla flag wyrażenia regularnego.

## <a name="syntax"></a>Składnia

```cpp
namespace regex_constants {
    enum syntax_option_type;
    enum match_flag_type;
    enum error_type;
}
```

## <a name="remarks"></a>Uwagi

Obszar nazw `regex_constants` hermetyzuje kilka typów flag i skojarzone z nimi wartości flag.

|||
|-|-|
|[error_type](#error_type)|Flagi do raportowania błędów składni wyrażenia regularnego.|
|[match_flag_type](#match_flag_type)|Flagi dla opcji dopasowywania wyrażeń regularnych.|
|[syntax_option_type](#syntax_option_type)|Flagi dotyczące wybierania opcji składni.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> regex

**Przestrzeń nazw:** std

## <a name="regex_constantserror_type"></a><a name="error_type"></a>regex_constants::error_type

Flagi do raportowania błędów składni wyrażenia regularnego.

```cpp
enum error_type
    {    // identify error
    error_collate,
    error_ctype,
    error_escape,
    error_backref,
    error_brack,
    error_paren,
    error_brace,
    error_badbrace,
    error_range,
    error_space,
    error_badrepeat,
    error_complexity,
    error_stack,
    error_parse,
    error_syntax
    };
```

### <a name="remarks"></a>Uwagi

Typ jest typem wyliczonym, który opisuje obiekt, który może zawierać flagi błędów. Odrębne wartości flagi to:

`error_backref`-- wyrażenie zawierało nieprawidłowe odwołanie wsteczne

`error_badbrace`-- wyrażenie zawierało nieprawidłową liczbę w wyrażeniu { }

`error_badrepeat`-- wyrażenie powtarzające (jedno z '*', '', '+', '{' w większości kontekstów) nie było poprzedzone wyrażeniem

`error_brace`-- wyrażenie zawierało niezrównane "{" lub "}"

`error_brack`-- wyrażenie zawierało niezrównane '[' lub ']'

`error_collate`-- wyrażenie zawierało nieprawidłową nazwę elementu sortującego

`error_complexity`-- próba meczu nie powiodła się, ponieważ była zbyt skomplikowana

`error_ctype`-- wyrażenie zawierało nieprawidłową nazwę klasy znaków

`error_escape`-- wyrażenie zawierało nieprawidłową sekwencję unikową

`error_paren`-- wyrażenie zawierało niezrównane "(" lub ")"

`error_parse`-- wyrażenie nie może przeanalizować

`error_range`-- wyrażenie zawierało nieprawidłowy specyfikator zakresu znaków

`error_space`-- analizowanie wyrażenia regularnego nie powiodło się, ponieważ nie było wystarczającej ilości dostępnych zasobów

`error_stack`-- próba dopasowania nie powiodła się, ponieważ nie było wystarczającej ilości pamięci

`error_syntax`-- analizowanie nie powiodło się w sprawie błędu składni

`error_backref`-- wyrażenie zawierało nieprawidłowe odwołanie wsteczne

## <a name="regex_constantsmatch_flag_type"></a><a name="match_flag_type"></a>regex_constants::match_flag_type

Flagi dla opcji dopasowywania wyrażeń regularnych.

```cpp
enum match_flag_type
    {    // specify matching and formatting rules
    match_default = 0x0000,
    match_not_bol = 0x0001,
    match_not_eol = 0x0002,
    match_not_bow = 0x0004,
    match_not_eow = 0x0008,
    match_any = 0x0010,
    match_not_null = 0x0020,
    match_continuous = 0x0040,
    match_prev_avail = 0x0100,
    format_default = 0x0000,
    format_sed = 0x0400,
    format_no_copy = 0x0800,
    format_first_only = 0x1000,
    _Match_not_null = 0x2000
    };
```

### <a name="remarks"></a>Uwagi

Typ jest typem maski bitowej, który opisuje opcje, które mają być używane podczas dopasowywania sekwencji tekstu do wyrażenia regularnego i formatowania flag, które mają być używane podczas zastępowania tekstu. Opcje można łączyć z . `|`

Opcje dopasowania to:

`match_default`

`match_not_bol`-- nie traktuj pierwszej pozycji w sekwencji docelowej jako początku wiersza

`match_not_eol`-- nie należy traktować pozycji przeszłej w sekwencji docelowej jako końca wiersza

`match_not_bow`-- nie traktuj pierwszej pozycji w sekwencji docelowej jako początku słowa

`match_not_eow`-- nie traktuj pozycji przeszłej w sekwencji docelowej jako końca wyrazu

`match_any`-- jeśli więcej niż jeden mecz jest możliwy, każde dopasowanie jest dopuszczalne

`match_not_null`-- nie traktuj pustej podsekwencji jako dopasowania

`match_continuous`-- nie wyszukuj dopasowań innych niż na początku sekwencji docelowej

`match_prev_avail` -- `--first`jest prawidłowym iteratorem; ignoruj `match_not_bol` i `match_not_bow` jeśli jest ustawiona

Flagi formatu to:

`format_default`-- użyj reguł formatu ECMAScript

`format_sed`-- użyj reguł formatu sed

`format_no_copy`-- nie kopiuj tekstu, który nie pasuje do wyrażenia regularnego

`format_first_only`-- nie szukaj meczów po pierwszym

## <a name="regex_constantssyntax_option_type"></a><a name="syntax_option_type"></a>regex_constants::syntax_option_type

Flagi dotyczące wybierania opcji składni.

```cpp
enum syntax_option_type
    {    // specify RE syntax rules
    ECMAScript = 0x01,
    basic = 0x02,
    extended = 0x04,
    awk = 0x08,
    grep = 0x10,
    egrep = 0x20,
    _Gmask = 0x3F,

    icase = 0x0100,
    nosubs = 0x0200,
    optimize = 0x0400,
    collate = 0x0800
    };
```

### <a name="remarks"></a>Uwagi

Typ jest typem maski bitowej, który opisuje specyfikatory języka i modyfikatory składni, które mają być używane podczas kompilowania wyrażenia regularnego. Opcje można łączyć z . `|` W ciągu jednego czasu należy używać więcej niż jednego specyfikatora języka.

Specyfikatory języka to:

`ECMAScript`-- skompiluj jako ECMAScript

`basic`-- skompiluj jako BRE

`extended`-- skompiluj jako ERE

`awk`-- skompiluj jak awk

`grep`-- skompiluj jako grep

`egrep`-- skompiluj jak egrep

Modyfikatory składni to:

`icase`-- sprawiają, że mecze niewrażliwe

`nosubs`-- implementaton nie musi śledzić zawartości grup przechwytywania

`optimize`-- implementacja powinna podkreślać szybkość dopasowywania, a nie szybkość kompilacji wyrażeń regularnych

`collate`-- spraw, aby mecze były zależne od ustawień regionalnych

## <a name="see-also"></a>Zobacz też

[\<>regex](../standard-library/regex.md)\
[Klasa regex_error](../standard-library/regex-error-class.md)\
[\<funkcje> regex](../standard-library/regex-functions.md)\
[Klasa regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operatorzy> regex](../standard-library/regex-operators.md)\
[Klasa regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Klasa regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)

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
ms.openlocfilehash: c8abca8109db9c781d63721b795feb01161fdb40
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419631"
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

Przestrzeń nazw `regex_constants` hermetyzuje kilka typów flag i skojarzonych z nimi wartości flag.

|||
|-|-|
|[error_type](#error_type)|Flagi dotyczące raportowania błędów składni wyrażeń regularnych.|
|[match_flag_type](#match_flag_type)|Flagi dla opcji dopasowania wyrażenia regularnego.|
|[syntax_option_type](#syntax_option_type)|Flagi do wybierania opcji składni.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyrażenia regularnego >

**Przestrzeń nazw:** std

## <a name="error_type"></a>regex_constants:: error_type

Flagi dotyczące raportowania błędów składni wyrażeń regularnych.

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

Typ to typ wyliczeniowy, który opisuje obiekt, który może zawierać flagi błędów. Wartości flag DISTINCT są następujące:

`error_backref` — wyrażenie zawiera nieprawidłowe odwołanie do tyłu

`error_badbrace` — wyrażenie zawiera nieprawidłową liczbę w wyrażeniu {}

`error_badrepeat`--wyrażenie Repeat (jedno z "*", "", "+", "{" w większości kontekstów) nie było poprzedzone wyrażeniem

`error_brace` — wyrażenie zawiera niedopasowany element "{" lub "}"

`error_brack` — wyrażenie zawiera niedopasowany element "[" lub "]"

`error_collate` — wyrażenie zawiera nieprawidłową nazwę elementu sortowania

`error_complexity` — próba dopasowania nie powiodła się, ponieważ była zbyt złożona

`error_ctype` — wyrażenie zawiera nieprawidłową nazwę klasy znaku

`error_escape` — wyrażenie zawiera nieprawidłową sekwencję ucieczki

`error_paren` — wyrażenie zawiera niedopasowany element "(" lub ")"

`error_parse` — nie można przeanalizować wyrażenia

`error_range` — wyrażenie zawiera nieprawidłowy specyfikator zakresu znaków

`error_space` — analizowanie wyrażenia regularnego nie powiodło się, ponieważ nie ma wystarczającej ilości dostępnych zasobów

`error_stack` — próba dopasowania nie powiodła się z powodu braku wystarczającej ilości dostępnej pamięci

`error_syntax` — analizowanie błędu nie powiodło się

`error_backref` — wyrażenie zawiera nieprawidłowe odwołanie do tyłu

## <a name="match_flag_type"></a>regex_constants:: match_flag_type

Flagi dla opcji dopasowania wyrażenia regularnego.

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

Typ jest typem maski bitowej opisującym opcje, które mają być używane podczas dopasowywania sekwencji tekstu względem wyrażenia regularnego i flag formatowania do użycia podczas zamiany tekstu. Opcje można łączyć z `|`.

Opcje dopasowania są następujące:

`match_default`

`match_not_bol` — nie Traktuj pierwszej pozycji w sekwencji docelowej jako początku wiersza

`match_not_eol`--nie należy traktować ostatniej-końcowego położenia w sekwencji docelowej jako końca wiersza

`match_not_bow` — nie Traktuj pierwszej pozycji w sekwencji docelowej jako początku wyrazu

`match_not_eow`--nie należy traktować ostatniej-końcowej pozycji w sekwencji docelowej jako końca wyrazu

`match_any`--jeśli możliwe jest spełnienie więcej niż jednego dopasowania

`match_not_null` — nie Traktuj pustej sekwencji jako dopasowania

`match_continuous` — nie wyszukuj dopasowań innych niż na początku sekwencji docelowej

`match_prev_avail` -- `--first` jest prawidłowym iteratorem; Ignoruj `match_not_bol` i `match_not_bow` Jeśli ustawione

Flagi formatu są następujące:

`format_default` — Użyj reguł formatu ECMAScript

`format_sed` — Użyj reguł formatu SED

`format_no_copy` — nie Kopiuj tekstu, który nie jest zgodny z wyrażeniem regularnym

`format_first_only` — nie wyszukuj pasujących elementów po pierwszej

## <a name="syntax_option_type"></a>regex_constants:: syntax_option_type

Flagi do wybierania opcji składni.

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

Typ jest typem maski bitowej opisującym specyfikatory języka i Modyfikatory składni, które mają być używane podczas kompilowania wyrażenia regularnego. Opcje można łączyć z `|`. W danym momencie nie można użyć więcej niż jednego specyfikatora języka.

Specyfikatory języka są następujące:

`ECMAScript` — Kompiluj jako ECMAScript

`basic` — Kompiluj jako BRE

`extended` — Kompiluj jako ERE

`awk` — Kompiluj jako AWK

`grep` — Kompiluj jako grep

`egrep` — Kompiluj jako egrep

Modyfikatory składni są następujące:

`icase` — nie dopasowuje wielkości liter

`nosubs` — implementaton nie musi śledzić zawartości grup przechwytywania

`optimize` — implementacja powinna wyróżnić szybkość dopasowywania, a nie szybkość kompilowania wyrażenia regularnego

`collate` — dopasowuje się do ustawień regionalnych

## <a name="see-also"></a>Zobacz też

[\<> wyrażeń regularnych](../standard-library/regex.md)\
\ [klasy regex_error](../standard-library/regex-error-class.md)
[\<funkcje > wyrażeń regularnych](../standard-library/regex-functions.md)\
\ [klasy regex_iterator](../standard-library/regex-iterator-class.md)
[\<operatory wyrażeń regularnych >](../standard-library/regex-operators.md)\
\ [klasy regex_token_iterator](../standard-library/regex-token-iterator-class.md)
\ [klasy regex_traits](../standard-library/regex-traits-class.md)
[\<wyrażenie regularne > Typedefs](../standard-library/regex-typedefs.md)

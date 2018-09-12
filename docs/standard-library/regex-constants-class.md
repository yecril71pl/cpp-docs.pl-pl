---
title: regex_constants — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e330cccb83ad702994b3d31d762cc0203e78de0
ms.sourcegitcommit: 27b5712badd09a09c499d887e2e4cf2208a28603
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44384998"
---
# <a name="regexconstants-namespace"></a>regex_constants — przestrzeń nazw

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

Przestrzeń nazw `regex_constants` hermetyzuje kilka typów flag i ich skojarzone wartości flag.

|||
|-|-|
|[error_type —](#error_type)|Flagi unikatowe dla raportowania błędów składni wyrażeń regularnych.|
|[match_flag_type —](#match_flag_type)|Flagi unikatowe dla wyrażenia regularnego, opcje dopasowania.|
|[syntax_option_type —](#syntax_option_type)|Flagi służąca do wybierania opcji składni.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyrażenia regularnego >

**Namespace:** standardowe

## <a name="error_type"></a>  regex_constants::error_type

Flagi unikatowe dla raportowania błędów składni wyrażeń regularnych.

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

Typ jest typem wyliczanym, opisująca obiekt, który może pomieścić flag błędów. Wartości odrębnych flagi są następujące:

`error_backref` --wyrażenie zawiera nieprawidłowe odwołanie do tyłu

`error_badbrace` --wyrażenie zawiera nieprawidłową liczbę w wyrażeniu {}

`error_badrepeat` — wyrażenia powtórzenia (jedną z "*", ","+"," {"w większości kontekstach) nie został poprzedzona przez wyrażenie

`error_brace` --wyrażenie zawiera Niedopasowany "{" lub "}"

`error_brack` --wyrażenie zawiera Niedopasowany "[" lub "]"

`error_collate` --wyrażenie zawiera nieprawidłową nazwę element sortujący

`error_complexity` --próby dopasowania nie powiodło się, ponieważ był zbyt złożony

`error_ctype` --wyrażenie zawiera nieprawidłowy znak nazwy klasy

`error_escape` --wyrażenie zawiera nieprawidłową sekwencję ucieczki

`error_paren` --wyrażenie zawiera Niedopasowany "(" lub")"

`error_parse` --Nie można przeanalizować wyrażenia

`error_range` --wyrażenie zawiera nieprawidłowy znak specyfikator zakresu

`error_space` --analizowanie wyrażeń regularnych nie powiodło się, ponieważ nie były dostępne za mało zasobów

`error_stack` --próby dopasowania nie powiodło się, ponieważ nie była dostępna wystarczająca ilość pamięci

`error_syntax` --analizowanie nie powiodło się na błąd składni

`error_backref` --wyrażenie zawiera nieprawidłowe odwołanie do tyłu

## <a name="match_flag_type"></a>  regex_constants::match_flag_type

Flagi unikatowe dla wyrażenia regularnego, opcje dopasowania.

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

Typ jest typem maski bitów, który w tym artykule opisano opcje, które będą używane podczas dopasowywania sekwencją tekstu względem wyrażenia regularnego i format flagi do użycia podczas zamieniania tekstu. Opcje można łączyć z `|`.

Dostępne są opcje dopasowania:

*match_default*<br/>

`match_not_bol` --nie Traktuj pierwszej pozycji w sekwencji docelowej, jak początek wiersza

`match_not_eol` --nie Traktuj przeszłości end pozycja w sekwencji docelowej, jako koniec wiersza

`match_not_bow` --nie Traktuj pierwszej pozycji w sekwencji docelowej, jak początku wyrazu

`match_not_eow` --nie Traktuj przeszłości end pozycja w sekwencji docelowej, jako koniec wyrazu

`match_any` — Jeśli możliwe jest więcej niż jedno dopasowanie jakiegokolwiek dopasowania jest dopuszczalne

`match_not_null` --nie Traktuj pusty podsekwencję jako dopasowanie

`match_continuous` --Nie wyszukuj dopasowania innych niż na początku sekwencji docelowej

`match_prev_avail` -- `--first` jest iteratorem prawidłowe; Ignoruj `match_not_bol` i `match_not_bow` Jeśli ustawić

Flagi formatu to:

`format_default` — Użyj reguły formatu ECMAScript

`format_sed` — Użyj reguły formatu sed

`format_no_copy` --nie Kopiuj tekst, który nie jest zgodny z wyrażeniem regularnym

`format_first_only` --Nie wyszukuj dopasowania po pierwszej

## <a name="syntax_option_type"></a>  regex_constants::syntax_option_type

Flagi służąca do wybierania opcji składni.

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

Typ jest typem maski bitów, który opisuje specyfikatory języka i składni modyfikatory, które ma być używany podczas kompilowania wyrażeń regularnych. Opcje można łączyć z `|`. Specyfikator nie więcej niż jednym języku powinny być używane w danym momencie.

Specyfikatory języka są następujące:

`ECMAScript` --skompilowana jako ECMAScript

`basic` --skompilowana jako BRE

`extended` --skompilowana jako ERE

`awk` --skompilowana jako awk

`grep` --skompilowana jako grep

`egrep` --skompilowana jako egrep

Dostępne są następujące Modyfikatory składni:

`icase` — upewnić dopasowania, bez uwzględniania wielkości liter

`nosubs` --przewidujące muszą nie zachować informacje o zawartości grup przechwytywania

`optimize` --implementacji podkreślić szybkość zgodnych, a nie szybkość kompilowania wyrażeń regularnych

`collate` --marki dopasowuje zależne od ustawień regionalnych

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)<br/>
[regex_error, klasa](../standard-library/regex-error-class.md)<br/>
[\<wyrażenie regularne > funkcji](../standard-library/regex-functions.md)<br/>
[regex_iterator, klasa](../standard-library/regex-iterator-class.md)<br/>
[\<wyrażenie regularne > operatorów](../standard-library/regex-operators.md)<br/>
[regex_token_iterator, klasa](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits, klasa](../standard-library/regex-traits-class.md)<br/>
[\<wyrażenie regularne > definicje typów](../standard-library/regex-typedefs.md)<br/>

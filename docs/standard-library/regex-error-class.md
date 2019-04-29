---
title: regex_error — Klasa
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: eed961ea698591935c22fc748ff79583ae636b27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62369621"
---
# <a name="regexerror-class"></a>regex_error — Klasa

Raporty obiektu basic_regex zła.

## <a name="syntax"></a>Składnia

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>Uwagi

Klasa opisuje obiekt wyjątku wyzwolony, aby zgłosić błąd w konstrukcji lub użytkowania `basic_regex` obiektu.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[regex_error](#regex_error)|Tworzy obiekt.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Kod](#code)|Zwraca kod błędu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyrażenia regularnego >

**Namespace:** standardowe

## <a name="example"></a>Przykład

```cpp
// std__regex__regex_error.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex_error paren(std::regex_constants::error_paren);

    try
        {
        std::regex rx("(a");
        }
    catch (const std::regex_error& rerr)
        {
        std::cout << "regex error: "
            << (rerr.code() == paren.code() ? "unbalanced parentheses" : "")
            << std::endl;
        }
    catch (...)
        {
        std::cout << "unknown exception" << std::endl;
        }

    return (0);
    }
```

```Output
regex error: unbalanced parentheses
```

## <a name="code"></a>  regex_error::Code

Zwraca kod błędu.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca wartość, która została przekazana do konstruktora obiektu.

## <a name="regex_error"></a>  regex_error::regex_error

Tworzy obiekt.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>Parametry

*Błąd*<br/>
Kod błędu.

### <a name="remarks"></a>Uwagi

Konstruktor konstruuje obiekt, który przechowuje wartość *błąd*.

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants, klasa](../standard-library/regex-constants-class.md)<br/>
[\<wyrażenie regularne > funkcji](../standard-library/regex-functions.md)<br/>
[regex_iterator, klasa](../standard-library/regex-iterator-class.md)<br/>
[\<wyrażenie regularne > operatorów](../standard-library/regex-operators.md)<br/>
[regex_token_iterator, klasa](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits, klasa](../standard-library/regex-traits-class.md)<br/>
[\<wyrażenie regularne > definicje typów](../standard-library/regex-typedefs.md)<br/>

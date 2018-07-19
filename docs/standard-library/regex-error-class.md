---
title: regex_error — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
dev_langs:
- C++
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7983857b3814f8ddd9c10ab37676bc2e87e9a59c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964148"
---
# <a name="regexerror-class"></a>regex_error — Klasa

Raporty obiektu basic_regex zła.

## <a name="syntax"></a>Składnia

```cpp
class regex_error
 : public std::runtime_error {
public:
    explicit regex_error(regex_constants::error_code error);

    regex_constants::error_code code() const;


};
```

## <a name="remarks"></a>Uwagi

Klasa opisuje obiekt wyjątku wyzwolony, aby zgłosić błąd w konstrukcji lub użytkowania `basic_regex` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyrażenia regularnego >

**Namespace:** standardowe

## <a name="code"></a>  regex_error::Code

Zwraca kod błędu.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca wartość, która została przekazana do konstruktora obiektu.

### <a name="example"></a>Przykład

```cpp
// std__regex__regex_error_code.cpp
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
            << (rerr.code() == paren.code()
                 "unbalanced parentheses" : "")
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

## <a name="regex_error"></a>  regex_error::regex_error

Tworzy obiekt.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>Parametry

*Błąd* kod błędu.

### <a name="remarks"></a>Uwagi

Konstruktor konstruuje obiekt, który przechowuje wartość *błąd*.

### <a name="example"></a>Przykład

```cpp
// std__regex__regex_error_construct.cpp
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
            << (rerr.code() == paren.code()
                 "unbalanced parentheses" : "")
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

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants, klasa](../standard-library/regex-constants-class.md)<br/>
[\<wyrażenie regularne > funkcji](../standard-library/regex-functions.md)<br/>
[regex_iterator, klasa](../standard-library/regex-iterator-class.md)<br/>
[\<wyrażenie regularne > operatorów](../standard-library/regex-operators.md)<br/>
[regex_token_iterator, klasa](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits, klasa](../standard-library/regex-traits-class.md)<br/>
[\<wyrażenie regularne > definicje typów](../standard-library/regex-typedefs.md)<br/>

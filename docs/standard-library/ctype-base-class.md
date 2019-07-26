---
title: ctype_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- locale/std::ctype_base
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
ms.openlocfilehash: f23b9528cf9a921e1d005756aa82751f3fdb745e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449357"
---
# <a name="ctypebase-class"></a>ctype_base — Klasa

Klasa służy jako klasa bazowa dla aspektów klasy szablonu [CType](../standard-library/ctype-class.md). Klasa bazowa dla klasy ctype, która jest używana do definiowania typów wyliczeń używanych w celu klasyfikowania lub testowania znaków indywidualnie lub w ramach całych zakresów.

## <a name="syntax"></a>Składnia

```cpp
struct ctype_base : public locale::facet
{
    enum
    {
        alnum,
        alpha,
        cntrl,
        digit,
        graph,
        lower,
        print,
        punct,
        space,
        upper,
        xdigit
    };
    typedef short mask;

    ctype_base( size_t _Refs = 0 );
    ~ctype_base();
};
```

## <a name="remarks"></a>Uwagi

Definiuje on maskę wyliczenia. Każda stała wyliczenia charakteryzuje inny sposób klasyfikowania znaków, zgodnie z definicją w funkcjach o podobnych nazwach zadeklarowanych \<w nagłówku CType. h >. Stałe są następujące:

- **miejsce** (funkcja [isspace](../standard-library/locale-functions.md#isspace))

- **Drukuj** (funkcja [isprint](../standard-library/locale-functions.md#isprint))

- **cntrl** (funkcja [iscntrl](../standard-library/locale-functions.md#iscntrl))

- **wielkie litery** (funkcja [IsUpper](../standard-library/locale-functions.md#isupper))

- **poniżej** (funkcja [IsLower](../standard-library/locale-functions.md#islower))

- **cyfra** (funkcja [](../standard-library/locale-functions.md#isdigit)iscyfra)

- **punct** (funkcja [ispunct](../standard-library/locale-functions.md#ispunct))

- **xdigit** (funkcja [isxdigit](../standard-library/locale-functions.md#isxdigit))

- **Alpha** (funkcja [isalpha](../standard-library/locale-functions.md#isalpha))

- **alnum** (funkcja [isalnum](../standard-library/locale-functions.md#isalnum))

- **Wykres** (funkcja [isgraf](../standard-library/locale-functions.md#isgraph))

Można scharakteryzowanie kombinacji klasyfikacji, ORing te stałe. W szczególności zawsze jest to prawdą, że **alnum** = = (  &#124; **cyfry** \) alfa i **Graph** \= \= \( **alnum** &#124; **punct**).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

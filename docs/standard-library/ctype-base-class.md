---
title: ctype_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- locale/std::ctype_base
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
ms.openlocfilehash: 83ef35f9fac438cfa217decf222abd365ff84269
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394185"
---
# <a name="ctypebase-class"></a>ctype_base — Klasa

Klasa służy jako klasa bazowa dla zestawów reguł klasy szablonu [ctype](../standard-library/ctype-class.md). Klasa bazowa dla klasy ctype, która jest używana do definiowania typów wyliczeń używanych w celu klasyfikowania lub testowania znaków indywidualnie lub w ramach całych zakresów.

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

Definiuje wyliczenie maski. Każda stała wyliczenia charakteryzuje inny sposób do klasyfikowania znaków, zgodnie z definicją funkcji o podobnych nazwach, zadeklarowany w nagłówku \<ctype.h >. Stałe są następujące:

- **miejsce** (funkcja [isspace](../standard-library/locale-functions.md#isspace))

- **Drukuj** (funkcja [isprint](../standard-library/locale-functions.md#isprint))

- **nacisnąć klawisze CTRL +** (funkcja [iscntrl](../standard-library/locale-functions.md#iscntrl))

- **Górny** (funkcja [isupper](../standard-library/locale-functions.md#isupper))

- **niższe** (funkcja [islower](../standard-library/locale-functions.md#islower))

- **cyfra** (funkcja [isdigit](../standard-library/locale-functions.md#isdigit))

- **punct** (funkcja [ispunct](../standard-library/locale-functions.md#ispunct))

- **xdigit** (funkcja [isxdigit](../standard-library/locale-functions.md#isxdigit))

- **alfa** (funkcja [isalpha](../standard-library/locale-functions.md#isalpha))

- **alnum** (funkcja [isalnum](../standard-library/locale-functions.md#isalnum))

- **Wykres** (funkcja [isgraph](../standard-library/locale-functions.md#isgraph))

Kombinacja klasyfikacji przez ORing można scharakteryzowania te stałe. W szczególności jest zawsze wartość true, który **alnum** == ( **alfa** &#124; **cyfrę** \) i **wykres** \= \= \( **alnum** &#124; **punct**).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

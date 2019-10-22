---
title: ctype_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- locale/std::ctype_base
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
ms.openlocfilehash: 4fac75d90c4e40a22e8ceae974c3f49c3d50a1d3
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688191"
---
# <a name="ctype_base-class"></a>ctype_base — Klasa

Klasa służy jako klasa bazowa dla aspektów szablonu klasy [CType](../standard-library/ctype-class.md). Klasa bazowa dla klasy ctype, która jest używana do definiowania typów wyliczeń używanych w celu klasyfikowania lub testowania znaków indywidualnie lub w ramach całych zakresów.

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

Definiuje on maskę wyliczenia. Każda stała wyliczenia charakteryzuje inny sposób klasyfikowania znaków, zgodnie z definicją w funkcjach o podobnych nazwach zadeklarowanych w nagłówku \<ctype. h >. Stałe są następujące:

- **Space** (funkcja [isspace](../standard-library/locale-functions.md#isspace))

- **Drukuj** (funkcja [isprint](../standard-library/locale-functions.md#isprint))

- **cntrl** (funkcja [iscntrl](../standard-library/locale-functions.md#iscntrl))

- **Upper** (funkcja [IsUpper](../standard-library/locale-functions.md#isupper))

- **Lower** (funkcja [IsLower](../standard-library/locale-functions.md#islower))

- **cyfra** (funkcja [iscyfra](../standard-library/locale-functions.md#isdigit))

- **punct** (funkcja [ispunct](../standard-library/locale-functions.md#ispunct))

- **xdigit** (funkcja [isxdigit](../standard-library/locale-functions.md#isxdigit))

- **alfa** (funkcja [isalpha](../standard-library/locale-functions.md#isalpha))

- **alnum** (funkcja [isalnum](../standard-library/locale-functions.md#isalnum))

- **Graph** (funkcja [isgraf](../standard-library/locale-functions.md#isgraph))

Można scharakteryzowanie kombinacji klasyfikacji, ORing te stałe. W szczególności zawsze jest to prawdą, że **alnum** = = ( **alfa** &#124; **cyfr** \) i **Graph** \= \= \( **alnum** &#124; **punct**).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

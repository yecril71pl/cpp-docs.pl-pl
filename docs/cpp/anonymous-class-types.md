---
title: Anonimowe typy klas
ms.date: 11/04/2016
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
ms.openlocfilehash: e227f48588c3c4f59c0d0bd28ab16178de159b58
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032086"
---
# <a name="anonymous-class-types"></a>Anonimowe typy klas

Klasy mogą być anonimowe — oznacza to, że mogą być zadeklarowane bez *identyfikatora.* Jest to przydatne podczas zastępowania nazwy klasy nazwą **typedef,** jak w następujący sposób:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

> [!NOTE]
> Użycie klas anonimowych pokazano w poprzednim przykładzie jest przydatne do zachowania zgodności z istniejącym kodem C. W niektórych kodach C użycie **typedef** w połączeniu z strukturami anonimowymi jest powszechne.

Klasy anonimowe są również przydatne, gdy chcesz, aby odwołanie do elementu członkowskiego klasy było wyświetlane tak, jakby nie było zawarte w osobnej klasie, jak w poniższej klasie:

```cpp
struct PTValue
{
    POINT ptLoc;
    union
    {
        int  iValue;
        long lValue;
    };
};

PTValue ptv;
```

W poprzednim kodzie `iValue` można uzyskać dostęp za pomocą operatora wyboru elementu członkowskiego obiektu (**. )** w następujący sposób:

```cpp
int i = ptv.iValue;
```

Klasy anonimowe podlegają pewnym ograniczeniom. (Aby uzyskać więcej informacji na temat anonimowych związków zawodowych, zobacz [Związki](../cpp/unions.md).) Klasy anonimowe:

- Nie może mieć konstruktora lub destruktora.

- Nie można przekazać jako argumenty do funkcji (chyba że sprawdzanie typu jest pokonany przy użyciu wielokropek).

- Nie można zwrócić jako zwracanych wartości z funkcji.

## <a name="anonymous-structs"></a>Struktury anonimowe

**Specyficzne dla firmy Microsoft**

Rozszerzenie Microsoft C umożliwia zadeklarowanie zmiennej struktury w innej strukturze bez nadawania jej nazwy. Te struktury zagnieżdżone są nazywane strukturami anonimowymi. C++ nie zezwala na struktury anonimowe.

Można uzyskać dostęp do członków struktury anonimowej, tak jakby byli członkami w strukturze zawierającej.

```cpp
// anonymous_structures.c
#include <stdio.h>

struct phone
{
    int  areacode;
    long number;
};

struct person
{
    char   name[30];
    char   gender;
    int    age;
    int    weight;
    struct phone;    // Anonymous structure; no name needed
} Jim;

int main()
{
    Jim.number = 1234567;
    printf_s("%d\n", Jim.number);
}
//Output: 1234567
```

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

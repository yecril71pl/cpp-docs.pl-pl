---
title: Anonimowe typy klas
ms.date: 11/04/2016
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
ms.openlocfilehash: 9cd27fb40522a07ce4591b654ee8a6dda53b4f28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456410"
---
# <a name="anonymous-class-types"></a>Anonimowe typy klas

Klasy mogą być anonimowy — czyli może być deklarowana bez *identyfikator*. Jest to przydatne podczas zamiany nazwy klasy za pomocą **typedef** nazwę, co przedstawiono poniżej:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

> [!NOTE]
>  Korzystanie z klasy anonimowe pokazano w poprzednim przykładzie przydaje się do zachowania zgodności z istniejącego kodu języka C. W kodzie C, niektóre użytkowania **typedef** w połączeniu z struktury anonimowe są powszechnie znane.

Klasy anonimowe są przydatne także w przypadku, gdy ma odwołanie do składowej klasy się tak, jakby nie były zawarte w osobnej klasy, tak jak poniżej:

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

W poprzednim kodzie `iValue` można uzyskać dostęp za pomocą operatora wyboru elementu członkowskiego obiektu (**.**) w następujący sposób:

```cpp
int i = ptv.iValue;
```

Klasy anonimowe podlegają pewne ograniczenia. (Aby uzyskać więcej informacji na temat związki anonimowe, zobacz [unie](../cpp/unions.md).) Klasy anonimowe:

- Nie może mieć Konstruktor lub destruktor.

- Nie można przekazać jako argumenty do funkcji (chyba że sprawdzania typu jest bezcelowe, przy użyciu wielokropka).

- Nie można zwrócić jako wartości zwracane przez funkcje.

## <a name="anonymous-structs"></a>Struktury anonimowe

### <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Rozszerzenie Microsoft C umożliwia przy deklarowaniu zmiennej struktury w obrębie innej struktury bez nadając mu nazwę. Te struktury zagnieżdżone są nazywane struktury anonimowe. C++ nie zezwala na struktury anonimowe.

Ma dostęp do członków struktury anonimowe, tak jakby były członkami w strukturze zawierającej.

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

**END specyficzny dla Microsoft**
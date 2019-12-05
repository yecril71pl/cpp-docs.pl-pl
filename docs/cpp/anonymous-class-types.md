---
title: Anonimowe typy klas
ms.date: 11/04/2016
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
ms.openlocfilehash: 815cc4a81addc673349a3133b24ed73cfe0207e2
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857674"
---
# <a name="anonymous-class-types"></a>Anonimowe typy klas

Klasy mogą być anonimowe — oznacza to, że można je zadeklarować bez *identyfikatora*. Jest to przydatne, gdy zastąpisz nazwę klasy z nazwą **typedef** , tak jak w poniższym:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

> [!NOTE]
>  Użycie anonimowych klas przedstawionych w poprzednim przykładzie jest przydatne w celu zachowania zgodności z istniejącym kodem C. W przypadku niektórych kodów języka C, użycie **typedef** w połączeniu ze strukturą anonimową jest rozpowszechnione.

Klasy anonimowe są również przydatne, gdy chcesz, aby odwołanie do składowej klasy pojawiało się tak, jakby nie było ono zawarte w osobnej klasie, tak jak w następujących przypadkach:

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

W poprzednim kodzie `iValue` można uzyskać dostęp za pomocą operatora wyboru elementu członkowskiego obiektu ( **.** ) w następujący sposób:

```cpp
int i = ptv.iValue;
```

Klasy anonimowe podlegają pewnym ograniczeniom. (Aby uzyskać więcej informacji na temat Unii anonimowych, zobacz [Unions](../cpp/unions.md)). Klasy anonimowe:

- Nie może mieć konstruktora ani destruktora.

- Nie można przesłać jako argumentów do funkcji (chyba że sprawdzanie typu jest obniżane przy użyciu wielokropka).

- Nie można zwrócić jako wartości zwracanej z funkcji.

## <a name="anonymous-structs"></a>Struktury anonimowe

**Microsoft Specific**

Rozszerzenie języka Microsoft C pozwala zadeklarować zmienną struktury w innej strukturze bez nadawania jej nazwy. Te zagnieżdżone struktury są nazywane struktury anonimowe. C++nie zezwala na anonimowe struktury.

Możesz uzyskać dostęp do elementów członkowskich struktury anonimowej, tak jakby były członkami w strukturze zawierającej.

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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

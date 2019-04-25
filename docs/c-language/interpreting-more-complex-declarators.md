---
title: Interpretowanie deklaratorów bardziej złożonych
ms.date: 11/04/2016
helpviewer_keywords:
- complex declarators
- interpreting complex declarators
ms.assetid: dd5b7019-c86d-4645-a5cc-21f834de6f4a
ms.openlocfilehash: 13c81728f02963863b641348b58380da099b0013
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232868"
---
# <a name="interpreting-more-complex-declarators"></a>Interpretowanie deklaratorów bardziej złożonych

Należy umieścić wszelkie deklaratora w nawiasach, aby określić konkretnego interpretacji "deklaratorów złożonych". Złożone deklaratora jest identyfikatorem kwalifikowana przez więcej niż jednej tablicy, wskaźnika lub modyfikator funkcji. Różne kombinacje tablicy, wskaźnika i funkcja modyfikatorów można zastosować do jednego identyfikatora. Ogólnie `typedef` można uproszczenie deklaracji. Zobacz [deklaracje Typedef](../c-language/typedef-declarations.md).

W interpretowanie deklaratorów złożonych, nawiasy i nawiasy (czyli Modyfikatory po prawej stronie identyfikatora) pierwszeństwo gwiazdki (czyli Modyfikatory identyfikator po lewej stronie). Jak nawiasy mają takie samo pierwszeństwo i skojarzone od lewej do prawej. Po w pełni interpretowane deklaratora Specyfikator typu zostanie zastosowana jako ostatni krok. Przy użyciu nawiasów można zastąpić domyślną kolejność skojarzenia i wymusić określonego interpretacji. Nigdy nie używaj nawiasów, jednak wokół nazwy identyfikatora samodzielnie. Może to być niemożliwe jako listy parametrów.

Jest to prosty sposób interpretowanie deklaratorów złożonych do ich czytania "od wewnątrz," wykonując następujące cztery kroki:

1. Rozpocznij od identyfikatora i "patrzą" bezpośrednio po prawej stronie dla nawiasów ani nawiasów (jeśli istnieje).

1. Interpretowanie tych nawiasów ani nawiasów, a następnie "patrzą" po lewej stronie, aby uzyskać gwiazdki.

1. Jeśli napotkasz prawy nawias okrągły na każdym etapie, przejdź wstecz i Zastosuj zasady 1 i 2 do wszystkiego w nawiasach.

1. Zastosuj Specyfikator typu.

    ```
    char *( *(*var)() )[10];
     ^   ^  ^ ^ ^   ^    ^
     7   6  4 2 1   3    5
    ```

W tym przykładzie kroki są ponumerowane w kolejności i może być interpretowany w następujący sposób:

1. Identyfikator `var` jest zadeklarowany jako

1. Wskaźnik do

1. funkcja zwracająca

1. Wskaźnik do

1. tablicy 10 elementów, które są

1. wskaźniki do

1. `char` wartości.

## <a name="examples"></a>Przykłady

Poniższe przykłady ilustrują innych złożonych deklaracji i pokazują, jak nawiasy mogą wpływać na znaczenie deklaracji.

```
int *var[5]; /* Array of pointers to int values */
```

Modyfikator tablicy ma wyższy priorytet niż modyfikator wskaźnika, więc `var` jest zadeklarowana w postaci tablicy. Modyfikator wskaźnika odnoszące się do typu elementów tablicy; w związku z tym, elementy tablicy są wskaźnikami do `int` wartości.

```
int (*var)[5]; /* Pointer to array of int values */
```

W tej deklaracji pod kątem `var`, nawiasy nadawały wskaźnika modyfikator wyższy priorytet niż modyfikator tablicy i `var` jest deklarowana jako wskaźnik do tablicy pięć `int` wartości.

```
long *var( long, long ); /* Function returning pointer to long */
```

Funkcja Modyfikatory również mają wyższy priorytet niż modyfikatorów wskaźników, więc tej deklaracji pod kątem `var` deklaruje `var` do funkcji zwracającej wskaźnik do **długie** wartość. Zadeklarowano funkcję do wykonania dwóch **długie** wartości jako argumenty.

```
long (*var)( long, long ); /* Pointer to function returning long */
```

Ten przykład jest podobny do poprzedniego. Nawiasy nadawały wskaźnika modyfikator wyższy priorytet niż modyfikator funkcji i `var` jest deklarowana jako wskaźnik do funkcji, która zwraca **długie** wartość. Ponownie funkcja przyjmuje dwa **długie** argumentów.

```
struct both       /* Array of pointers to functions */
{                 /*   returning structures         */
    int a;
    char b;
} ( *var[5] )( struct both, struct both );
```

Elementy tablicy nie może być funkcji, ale ta deklaracja pokazuje, jak zadeklarować tablicę wskaźników do funkcji, zamiast tego. W tym przykładzie `var` jest zadeklarowana w postaci tablicy pięć wskaźników do funkcji, które zwracają struktury za pomocą dwóch członków. Argumenty funkcji są deklarowane jako dwie struktury za pomocą tego samego typu struktury `both`. Należy pamiętać, że nawiasy otaczające `*var[5]` są wymagane. Bez nich deklaracja jest niedozwolona próba jest zadeklarowanie tablicy funkcji, jak pokazano poniżej:

```
/* ILLEGAL */
struct both *var[5](struct both, struct both);
```

Poniższa instrukcja deklaruje tablicę wskaźników.

```
unsigned int *(* const *name[5][10] ) ( void );
```

`name` Tablica zawiera elementy 50 zorganizowane w tablicy wielowymiarowej. Elementy są wskaźnikami do wskaźnika, który jest stałą. Stałe wskazuje ten wskaźnik do funkcji, która nie ma parametrów i zwraca wskaźnik do typu bez znaku.

W tym przykładzie dalej jest funkcji zwracającej wskaźnik do tablicy trzech **double** wartości.

```
double ( *var( double (*)[3] ) )[3];
```

W tym oświadczeniu funkcja zwraca wskaźnik do tablicy, od funkcji zwracających tablice są niedozwolone. W tym miejscu `var` został zadeklarowany jako funkcji zwracającej wskaźnik do tablicy trzech **double** wartości. Funkcja `var` przyjmuje jeden argument. Argument, takich jak wartość zwracana jest wskaźnikiem do tablicy trzech **double** wartości. Typ argumentu jest nadawana przez złożony *abstrakcyjny declarator*. Nawiasy wokół gwiazdki w typ argumentu są wymagane; bez nich typ argumentu będzie tablica trzy wskaźników do **double** wartości. Dyskusję na temat i przykłady deklaratory abstrakcyjne, zobacz [deklaratory abstrakcyjne](../c-language/c-abstract-declarators.md).

```
union sign         /* Array of arrays of pointers */
{                  /* to pointers to unions       */
     int x;
     unsigned y;
} **var[5][5];
```

Jak pokazano w powyższym przykładzie, wskaźnik może wskazywać na inny wskaźnik, a Tablica może zawierać tablice jako elementy. W tym miejscu `var` jest tablicą pięć kolejnych elementów. Każdy element jest 5 elementowej tablicy wskaźników do wskaźników do złożenia za pomocą dwóch członków.

```
union sign *(*var[5])[5]; /* Array of pointers to arrays
                             of pointers to unions        */
```

Ten przykład pokazuje, jak zmienia się znaczenie deklaracji umieszczania nawiasów. W tym przykładzie `var` jest 5 elementowej tablicy wskaźników do 5 elementowej tablice wskaźników do Unii. Aby uzyskać przykłady sposobów użycia `typedef` Aby uniknąć złożonych deklaracji, zobacz [deklaracje Typedef](../c-language/typedef-declarations.md).

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)

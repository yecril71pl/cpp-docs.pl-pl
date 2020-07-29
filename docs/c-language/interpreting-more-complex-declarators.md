---
title: Interpretowanie deklaratorów bardziej złożonych
ms.date: 11/04/2016
helpviewer_keywords:
- complex declarators
- interpreting complex declarators
ms.assetid: dd5b7019-c86d-4645-a5cc-21f834de6f4a
ms.openlocfilehash: 385392ea8836998e71584d02bd0ee4478fb774a0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199909"
---
# <a name="interpreting-more-complex-declarators"></a>Interpretowanie deklaratorów bardziej złożonych

Można ująć dowolne deklarator w nawiasach, aby określić konkretną interpretację "złożone deklarator". Złożony deklarator jest identyfikatorem kwalifikowanym przez więcej niż jedną tablicę, wskaźnik lub modyfikator funkcji. Można zastosować różne kombinacje modyfikatorów tablicowych, wskaźników i funkcji do pojedynczego identyfikatora. Zwykle **`typedef`** może służyć do uproszczenia deklaracji. Zobacz [deklaracje typedef](../c-language/typedef-declarations.md).

W interpretacji złożonej deklaratory, nawiasy i nawiasy (czyli Modyfikatory z prawej strony identyfikatora) mają pierwszeństwo przed gwiazdkami (czyli modyfikatorami z lewej strony identyfikatora). Nawiasy i nawiasy mają takie samo pierwszeństwo i są kojarzone od lewej do prawej. Po pełnej interpretacji deklarator specyfikator typu jest stosowany jako ostatni krok. Za pomocą nawiasów można zastąpić domyślny porządek kojarzenia i wymusić określoną interpretację. Nigdy nie używaj nawiasów, jednak jednocześnie wokół nazwy identyfikatora. Może to być błędnie interpretowane jako lista parametrów.

Prosty sposób interpretacji złożonych Deklaratory polega na ich odczytaniu "z wnętrza", wykonując następujące cztery kroki:

1. Zacznij od identyfikatora i poszukaj bezpośrednio w prawo dla nawiasów lub nawiasów (jeśli istnieją).

1. Interpretuj te nawiasy lub nawiasy, a następnie poszukaj w lewej części gwiazdki.

1. Jeśli napotkasz prawy nawias na dowolnym etapie, wróć i zastosuj reguły 1 i 2 do wszystkiego w nawiasach.

1. Zastosuj specyfikator typu.

    ```
    char *( *(*var)() )[10];
     ^   ^  ^ ^ ^   ^    ^
     7   6  4 2 1   3    5
    ```

W tym przykładzie kroki są numerowane w kolejności i mogą być interpretowane w następujący sposób:

1. Identyfikator `var` jest zadeklarowany jako

1. wskaźnik do

1. funkcja zwracająca

1. wskaźnik do

1. Tablica 10 elementów, które są

1. wskaźniki do

1. **`char`** wartością.

## <a name="examples"></a>Przykłady

Poniższe przykłady ilustrują inne złożone deklaracje i pokazują, jak nawiasy mogą wpływać na znaczenie deklaracji.

```
int *var[5]; /* Array of pointers to int values */
```

Modyfikator tablicy ma wyższy priorytet niż modyfikator wskaźnika, więc `var` jest zadeklarowany jako tablica. Modyfikator wskaźnika ma zastosowanie do typu elementów tablicy; w związku z tym elementy tablicy są wskaźnikami do **`int`** wartości.

```
int (*var)[5]; /* Pointer to array of int values */
```

W tej deklaracji dla `var` , nawiasy dają modyfikator wskaźnika wyższy priorytet niż modyfikator tablicy i `var` jest zadeklarowany jako wskaźnik do tablicy pięciu **`int`** wartości.

```
long *var( long, long ); /* Function returning pointer to long */
```

Modyfikatory funkcji mają również wyższy priorytet niż Modyfikatory wskaźnika, więc ta deklaracja `var` deklaruje jako `var` funkcję zwracającą wskaźnik do **`long`** wartości. Funkcja jest zadeklarowana, aby przyjmować dwie **`long`** wartości jako argumenty.

```
long (*var)( long, long ); /* Pointer to function returning long */
```

Ten przykład jest podobny do poprzedniego. Nawiasy dają modyfikator wskaźnika wyższy priorytet niż modyfikator funkcji i `var` jest zadeklarowany jako wskaźnik do funkcji, która zwraca **`long`** wartość. Ponownie funkcja przyjmuje dwa **`long`** argumenty.

```
struct both       /* Array of pointers to functions */
{                 /*   returning structures         */
    int a;
    char b;
} ( *var[5] )( struct both, struct both );
```

Elementy tablicy nie mogą być funkcjami, ale ta deklaracja pokazuje, jak zadeklarować tablicę wskaźników do funkcji. W tym przykładzie `var` jest zadeklarowany jako tablica pięciu wskaźników do funkcji, które zwracają struktury z dwoma elementami członkowskimi. Argumenty funkcji są deklarowane jako dwie struktury z tym samym typem struktury, `both` . Należy zauważyć, że nawiasy otaczające `*var[5]` są wymagane. Bez nich, deklaracja jest niedozwoloną próbą zadeklarować tablicę funkcji, jak pokazano poniżej:

```
/* ILLEGAL */
struct both *var[5](struct both, struct both);
```

Poniższa instrukcja deklaruje tablicę wskaźników.

```
unsigned int *(* const *name[5][10] ) ( void );
```

`name`Tablica zawiera 50 elementów zorganizowanych w tablicę wielowymiarową. Elementy są wskaźnikami do wskaźnika, który jest stałą. Ten stały wskaźnik wskazuje funkcję, która nie ma parametrów i zwraca wskaźnik do niepodpisanego typu.

Ten następny przykład to funkcja zwracająca wskaźnik do tablicy trzech **`double`** wartości.

```
double ( *var( double (*)[3] ) )[3];
```

W tej deklaracji funkcja zwraca wskaźnik do tablicy, ponieważ funkcje zwracające tablice są niedozwolone. W tym miejscu `var` zadeklarowano jako funkcję zwracającą wskaźnik do tablicy trzech **`double`** wartości. Funkcja `var` przyjmuje jeden argument. Argument, podobny do wartości zwracanej, jest wskaźnikiem do tablicy trzech **`double`** wartości. Typ argumentu jest określony przez złożone *abstrakcyjne-deklarator*. Nawiasy wokół gwiazdki w typie argumentu są wymagane; bez nich typ argumentu będzie tablicą trzech wskaźników do **`double`** wartości. Aby zapoznać się z omówieniem i przykładami abstrakcyjnych deklaratory, zobacz [abstract Deklaratory](../c-language/c-abstract-declarators.md).

```
union sign         /* Array of arrays of pointers */
{                  /* to pointers to unions       */
     int x;
     unsigned y;
} **var[5][5];
```

Jak pokazano na powyższym przykładzie, wskaźnik może wskazywać na inny wskaźnik, a tablica może zawierać tablice jako elementy. Poniżej `var` znajduje się tablica pięciu elementów. Każdy element jest tablicą składającą się z pięciu elementów, która jest wskaźnikiem do Unii zawierających dwa elementy członkowskie.

```
union sign *(*var[5])[5]; /* Array of pointers to arrays
                             of pointers to unions        */
```

Ten przykład pokazuje, jak umieszczanie nawiasów zmienia znaczenie deklaracji. W tym przykładzie `var` jest to pięć-elementowa tablica wskaźników do pięciu elementów wskaźników do Unii. Aby zapoznać się z przykładami użycia **`typedef`** programu w celu uniknięcia złożonych deklaracji, zobacz [deklaracje typedef](../c-language/typedef-declarations.md).

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)

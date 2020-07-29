---
title: Deklaracje wskaźników
ms.date: 11/04/2016
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
ms.openlocfilehash: 31d7e30859537fed1b18f6d30302d83248e17e74
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211765"
---
# <a name="pointer-declarations"></a>Deklaracje wskaźników

*Deklaracja wskaźnika* nazywa zmienną wskaźnika i określa typ obiektu, do którego należy zmienna. Zmienna zadeklarowana jako wskaźnik przechowuje adres pamięci.

## <a name="syntax"></a>Składnia

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>wybór</sub> wskaźnika *Direct-deklarator*

*deklarator Direct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatora*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *deklarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator* **[** *wybór wyrażenia stałego*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator* **(** *Typ parametru-list* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator* **(** *opt z listą identyfikatorów*<sub>opt</sub> **)**

*wskaźnik*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*Typ kwalifikatora —*<sub>wybór</sub> listy<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*Typ kwalifikatora —*<sub>opt</sub> *wskaźnik* wyboru listy

*kwalifikator typu-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kwalifikator typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kwalifikator typu —* *kwalifikator typu* list

*Specyfikator typu* zwraca typ obiektu, który może być dowolnego typu podstawowego, struktury lub Unii. Zmienne wskaźnika mogą również wskazywać funkcje, tablice i inne wskaźniki. (Aby uzyskać informacje na temat deklarowania i interpretowania bardziej złożonych typów wskaźnikowych, zobacz [Interpretowanie bardziej złożonej Deklaratory](../c-language/interpreting-more-complex-declarators.md)).

Tworząc *specyfikator typu* **`void`** , można opóźnić specyfikację typu, do którego odwołuje się wskaźnik. Taki element jest określany jako "wskaźnik do **`void`** " i jest zapisywana jako `void *` . Zmienna zadeklarowana jako wskaźnik do elementu *void* może służyć do wskazywania obiektu dowolnego typu. Jednak aby wykonać większość operacji na wskaźniku lub obiekt, do którego wskazuje, typ, do którego wskazuje punkt, musi być jawnie określony dla każdej operacji. (Zmienne typu **`char`** <strong>\*</strong> i typ **`void`** <strong>\*</strong> są zgodne z przypisaniem bez rzutowania typu. Taką konwersję można wykonać przy użyciu rzutowania typu (zobacz [Konwersje rzutowania typów](../c-language/type-cast-conversions.md) , aby uzyskać więcej informacji).

*Kwalifikatorem typu* może być albo lub lub **`const`** **`volatile`** . Określają one odpowiednio, że wskaźnik nie może zostać zmodyfikowany przez sam program ( **`const`** ) lub że wskaźnik może być uzasadniony przez jakiś proces poza kontrolą programu ( **`volatile`** ). (Zobacz [kwalifikatory typów](../c-language/type-qualifiers.md) , aby uzyskać więcej informacji na temat **`const`** i **`volatile`** .)

*Deklarator* nazywa zmienną i może zawierać modyfikator typu. Na przykład jeśli *deklarator* reprezentuje tablicę, typ wskaźnika jest modyfikowany jako wskaźnik do tablicy.

Można zadeklarować wskaźnik do struktury, Unii lub typu wyliczeniowy przed zdefiniowaniem struktury, Unii lub typu wyliczenia. Wskaźnik deklaruje się za pomocą tagu Structure lub Union, jak pokazano w poniższych przykładach. Takie deklaracje są dozwolone, ponieważ kompilator nie musi znać rozmiaru struktury lub Unii, aby przydzielić miejsce dla zmiennej wskaźnikowej.

## <a name="examples"></a>Przykłady

Poniższe przykłady ilustrują deklaracje wskaźnika.

```
char *message; /* Declares a pointer variable named message */
```

Wskaźnik *komunikatu* wskazuje na zmienną **`char`** typu.

```
int *pointers[10];  /* Declares an array of pointers */
```

Tablica *wskaźników* ma 10 elementów; Każdy element jest wskaźnikiem do zmiennej **`int`** typu.

```
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */
```

Zmienna *wskaźnik* wskazuje tablicę zawierającą 10 elementów. Każdy element w tej tablicy ma **`int`** Typ.

```
int const *x;      /* Declares a pointer variable, x,
                      to a constant value */
```

Wskaźnik *x* można zmodyfikować w taki sposób, aby wskazywał inną **`int`** wartość, ale wartość, do której punkty IT nie mogą być modyfikowane.

```
const int some_object = 5 ;
int other_object = 37;
int *const y = &fixed_object;
int volatile *const z = &some_object;
int *const volatile w = &some_object;
```

Zmienna *y* w tych deklaracjach jest zadeklarowana jako stały wskaźnik do **`int`** wartości. Wartość, która wskazuje na, może być modyfikowana, ale sam wskaźnik musi zawsze wskazywać na tę samą lokalizację: adres *fixed_object*. Podobnie, *z* jest wskaźnikiem stałym, ale jest również zadeklarowany jako wskazujący, **`int`** którego wartość nie może być modyfikowana przez program. Dodatkowy specyfikator **`volatile`** wskazuje, że mimo że wartość typu **const int** wskazywanego przez *z* nie może zostać zmodyfikowana przez program, może być w sposób wiarygodny zmodyfikowany przez proces uruchomiony współbieżnie przy użyciu programu. Deklaracja *w* programie określa, że program nie może zmienić wartości wskazywanej przez program i że nie można zmodyfikować wskaźnika.

```
struct list *next, *previous; /* Uses the tag for list */
```

Ten przykład deklaruje dwie zmienne wskaźnikowe, *Next* i *Previous*, które wskazują na *listę*typów struktury. Ta deklaracja może wystąpić przed definicją typu struktury *listy* (patrz następny przykład), o ile definicja typu *listy* ma taki sam wgląd jak Deklaracja.

```
struct list
{
    char *token;
    int count;
    struct list *next;
} line;
```

*Wiersz* zmiennej ma typ struktury o nazwie *Lista*. Typ struktury *listy* ma trzy składowe: pierwszy element członkowski jest wskaźnikiem do **`char`** wartości, drugi jest **`int`** wartością, a trzeci jest wskaźnikiem do innej struktury *listy* .

```
struct id
{
    unsigned int id_no;
    struct name *pname;
} record;
```

*Rekord* zmiennej ma *Identyfikator*typu struktury. Należy zauważyć, że *pname* jest zadeklarowany jako wskaźnik do innego typu struktury o nazwie *name*. Ta deklaracja może wystąpić przed zdefiniowaniem typu *nazwy* .

## <a name="see-also"></a>Zobacz także

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)

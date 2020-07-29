---
title: Deklaratory i deklaracje zmiennych
ms.date: 11/04/2016
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
ms.openlocfilehash: b20cde6982e99dedaff59518b71c041233a01dd8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226454"
---
# <a name="declarators-and-variable-declarations"></a>Deklaratory i deklaracje zmiennych

W pozostałej części tej sekcji opisano formę i znaczenie deklaracji typów zmiennych podsumowanych na tej liście. W szczególności pozostałe sekcje wyjaśniają, jak zadeklarować następujące elementy:

|Typ zmiennej|Opis|
|----------------------|-----------------|
|[Zmienne proste](../c-language/simple-variable-declarations.md)|Zmienne pojedynczej wartości z typem całkowitym lub zmiennoprzecinkowym|
|[Macierze](../c-language/array-declarations.md)|Zmienne złożone z kolekcji elementów tego samego typu|
|[Wskaźniki](../c-language/pointer-declarations.md)|Zmienne wskazujące na inne zmienne i zawierają lokalizacje zmiennych (w postaci adresów), a nie wartości|
|[Zmienne wyliczenia](../c-language/c-enumeration-declarations.md)|Proste zmienne z typem całkowitym zawierającym jedną wartość z zestawu nazwanych stałych całkowitych|
|[Struktury](../c-language/structure-declarations.md)|Zmienne złożone z kolekcji wartości, które mogą mieć różne typy|
|[Unie](../c-language/union-declarations.md)|Zmienne złożone z kilku wartości różnych typów, które zajmują to samo miejsce w magazynie|

Deklarator jest częścią deklaracji, która określa nazwę, która ma zostać wprowadzona do programu. Może zawierać modyfikatory, takie jak <strong>\*</strong> (wskaźnik do) i dowolne z słów kluczowych konwencji wywoływania firmy Microsoft.

**Specyficzne dla firmy Microsoft**

W deklarator

```C
__declspec(thread) char *var;
```

**`char`** jest specyfikatorem typu `__declspec(thread)` i `*` jest modyfikatorem i `var` jest nazwą identyfikatora.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Używasz Deklaratory do deklarowania tablic wartości, wskaźników do wartości, a funkcje zwracają wartości określonego typu. Deklaratory pojawiają się w deklaracjach tablicowych i wskaźnikowych opisanych w dalszej części tej sekcji.

## <a name="syntax"></a>Składnia

*deklarator*:<br/>
&nbsp;&nbsp;*pointer*<sub>wybór</sub> wskaźnika *Direct-deklarator*

*deklarator Direct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatora*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *deklarator*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator***[***wybór wyrażenia stałego*<sub>opt</sub> **]**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator*  **(**  *Typ parametru-list*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator***(***opt z listą identyfikatorów*<sub>opt</sub> **)**    

*wskaźnik*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*Typ kwalifikatora —*<sub>wybór</sub> listy<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*Typ kwalifikatora —*<sub>opt</sub> *wskaźnik* wyboru listy

*kwalifikator typu-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kwalifikator typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kwalifikator typu — kwalifikator typu list*

> [!NOTE]
> Zapoznaj się z składnią *deklaracji* w temacie [Omówienie deklaracji](../c-language/overview-of-declarations.md) lub [składni języka C](../c-language/c-language-syntax-summary.md) dla składni odwołującej się do *deklarator*.

Gdy deklarator składa się z niezmodyfikowanego identyfikatora, zadeklarowany element ma typ podstawowy. Jeśli gwiazdka ( <strong>\*</strong> ) pojawia się po lewej stronie identyfikatora, typ jest modyfikowany do typu wskaźnika. Jeśli po identyfikatorze następuje nawias (**[]**), typ jest modyfikowany do typu tablicy. Jeśli po stronie identyfikatora następuje nawias, typ jest modyfikowany do typu funkcji. Aby uzyskać więcej informacji na temat interpretacji pierwszeństwa w deklaracjach, zobacz [Interpretowanie bardziej złożonej Deklaratory](../c-language/interpreting-more-complex-declarators.md).

Każdy deklarator deklaruje co najmniej jeden identyfikator. Element Deklarator musi zawierać specyfikator typu jako kompletną deklarację. Specyfikator typu zawiera typ elementów typu tablicy, typ obiektu, do którego odnosi się typ wskaźnika lub typ zwracany funkcji.

Deklaracje [tablic](../c-language/array-declarations.md) i [wskaźników](../c-language/pointer-declarations.md) zostały omówione bardziej szczegółowo w dalszej części tej sekcji. Poniższe przykłady ilustrują kilka prostych form Deklaratory:

```C
int list[20]; // Declares an array of 20 int values named list
char *cp;     // Declares a pointer to a char value
double func( void ); // Declares a function named func, with no
                     // arguments, that returns a double value
int *aptr[10] // Declares an array of 10 pointers
```

**Specyficzne dla firmy Microsoft**

Kompilator języka Microsoft C nie ogranicza liczby deklaratory, która może modyfikować typ arytmetyczny, struktury lub Unii. Liczba jest ograniczona tylko przez dostępną pamięć.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)

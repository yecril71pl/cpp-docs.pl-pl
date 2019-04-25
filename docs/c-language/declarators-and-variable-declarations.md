---
title: Deklaratory i deklaracje zmiennych
ms.date: 11/04/2016
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
ms.openlocfilehash: 928de4b1724577a9fdb282f5109b4b5d0b31c4e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234533"
---
# <a name="declarators-and-variable-declarations"></a>Deklaratory i deklaracje zmiennych

Pozostałej części tej sekcji opisano formularza i znaczenie deklaracje zmiennych typów podsumowywane na tej liście. W szczególności pozostałych sekcjach wyjaśniono, jak zadeklarować następujące czynności:

|Typ zmiennej|Opis|
|----------------------|-----------------|
|[Zmienne proste](../c-language/simple-variable-declarations.md)|Zmienne pojedynczą wartość z typu całkowitego lub zmiennoprzecinkowego|
|[Tablice](../c-language/array-declarations.md)|Zmienne składa się z kolekcją elementów tego samego typu|
|[Wskaźniki](../c-language/pointer-declarations.md)|Zmienne, które wskazują inne zmienne i zawierać zmienną lokalizacji (w formie adresów) zamiast wartości|
|[Wyliczenie zmiennych](../c-language/c-enumeration-declarations.md)|Proste zmiennych o całkowitego wpisz jednej wartości z zestawu stałe nazwane całkowite wstrzymanie|
|[Struktury](../c-language/structure-declarations.md)|Składające się z kolekcji wartości, które mogą mieć różne typy zmiennych|
|[Unie](../c-language/union-declarations.md)|Zmienne składa się z kilku wartości różnych typów, które zajmują się tego samego miejsca do magazynowania|

Deklarator jest częścią deklaracji, która określa nazwę, która ma zostać wprowadzony do programu. Modyfikatory może obejmować takie jak <strong>\*</strong> (wskaźnik-do) oraz wszelkie słowa kluczowe Konwencja wywoływania firmy Microsoft.

**Microsoft Specific**

W deklaratora

```C
__declspec(thread) char *var;
```

`char` Specyfikator typu jest `__declspec(thread)` i `*` są modyfikatorami, i `var` jest nazwa identyfikatora.

**END specyficzny dla Microsoft**

Deklaratory umożliwia deklarują tablice wartości, wskaźniki do wartości i funkcji zwracających wartości określonego typu. Deklaratory pojawiają się w deklaracji tablicy i wskaźnik opisanym w dalszej części tej sekcji.

## <a name="syntax"></a>Składnia

*deklarator*:<br/>
&nbsp;&nbsp;*wskaźnik*<sub>zoptymalizowany pod kątem</sub> *deklaratora bezpośrednie*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(***deklaratora***)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **[** *wyrażenie_stałe*<sub>zoptymalizowany pod kątem</sub> **]** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy identyfikatorów*<sub>zoptymalizowany pod kątem</sub> **)**

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Lista typów kwalifikator*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Lista typów kwalifikator*<sub>zoptymalizowany pod kątem</sub> *wskaźnika*

*Lista typów kwalifikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu Lista w przypadku kwalifikator typu*

> [!NOTE]
> Wyświetlić składnię *deklaracji* w [Przegląd deklaracji](../c-language/overview-of-declarations.md) lub [podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md) dla składni, która odwołuje się do *deklaratora*.

Po deklaratorze składa się z identyfikatora zostały zmodyfikowane, element został zadeklarowany ma typ podstawowy. Jeśli znak gwiazdki (<strong>\*</strong>) pojawia się po lewej stronie identyfikator, typ został zmodyfikowany na typ wskaźnika. Jeśli identyfikator następuje nawiasy kwadratowe (**[**), typ został zmodyfikowany typ tablicy. Jeśli identyfikator następuje nawiasy, typ został zmodyfikowany do typu funkcji. Aby uzyskać więcej informacji na temat interpretacji pierwszeństwo w obrębie deklaracji zobacz [interpretowanie Deklaratorów bardziej złożonych](../c-language/interpreting-more-complex-declarators.md).

Każdy deklarator deklaruje co najmniej jeden identyfikator. Deklarator musi zawierać specyfikatora typu, aby mieć pełną deklarację. Specyfikator typu zawiera typ elementów typu tablicowego, typu obiektu według typu wskaźnika lub zwracany typ funkcji.

[Tablica](../c-language/array-declarations.md) i [wskaźnik](../c-language/pointer-declarations.md) deklaracje zostały omówione bardziej szczegółowo w dalszej części tej sekcji. Poniższe przykłady ilustrują kilka prostych formularzy deklaratorów:

```C
int list[20]; // Declares an array of 20 int values named list
char *cp;     // Declares a pointer to a char value
double func( void ); // Declares a function named func, with no
                     // arguments, that returns a double value
int *aptr[10] // Declares an array of 10 pointers
```

**Microsoft Specific**

Kompilator Microsoft C: nie ogranicza liczby deklaratory, które można modyfikować operacje arytmetyczne, struktury lub Unii. Liczba jest ograniczona jedynie ilością dostępnej pamięci.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)

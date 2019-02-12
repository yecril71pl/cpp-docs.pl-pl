---
title: Proste deklaracje zmiennej
ms.date: 11/04/2016
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
ms.openlocfilehash: 27710dabe512332564ee557a9d022457d9fddc5c
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149989"
---
# <a name="simple-variable-declarations"></a>Proste deklaracje zmiennej

Deklaracja zmiennej prosty, Najprostszą formą deklaratora bezpośrednich, określa nazwę i typ zmiennej. Określa również klasę magazynu w zmiennej i typ danych.

Klasy magazynu lub typów (lub obie) są wymagane w deklaracji zmiennej. Bez typu zmienne (takie jak `var;`) generowanie ostrzeżenia.

## <a name="syntax"></a>Składnia

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wskaźnik*<sub>zoptymalizowany pod kątem</sub> *deklaratora bezpośrednie*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*Identyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator* *nie cyfrą*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator* *cyfra*

Dla arytmetyczne, struktury, złożenia, wyliczenia i typu void, a dla typów reprezentowanych przez `typedef` nazwy, proste deklaratory mogą być używane w deklaracji, ponieważ Specyfikator typu dostarcza Pisownia informacje. Wskaźnik, tablicy i typy funkcji wymaga deklaratorów bardziej skomplikowane.

Można użyć identyfikatorów rozdzielonych przecinkami (**,**) do określania wielu zmiennych w tej samej deklaracji. Wszystkie zmienne zdefiniowane w deklaracji mają ten sam typ podstawowy. Na przykład:

```C
int x, y;        /* Declares two simple variables of type int */
int const z = 1; /* Declares a constant value of type int */
```

Zmienne `x` i `y` mogą przechowywać dowolne wartości w zestawie, określone przez `int` typu dla danego wdrożenia. Prosty obiekt `z` jest ustawiana na wartość 1 i nie można modyfikować.

Jeśli deklaracja `z` miał niezainicjowanej zmiennej statycznej czy był w zakresie pliku otrzyma początkowa wartość 0, a ta wartość będzie niemodyfikowalnych.

```C
unsigned long reply, flag; /* Declares two variables
                              named reply and flag     */
```

W tym przykładzie oba zmienne, `reply` i `flag`, mają `unsigned long` wpisz i przechowywania wartości całkowitych bez znaku.

## <a name="see-also"></a>Zobacz także

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)

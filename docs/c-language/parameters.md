---
title: Parametry
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipses (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
ms.openlocfilehash: 0652fe6076899020050d94378649018721b4b188
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147233"
---
# <a name="parameters"></a>Parametry

Argumenty są nazwy wartości przekazanych do funkcji przez wywołanie funkcji. Parametry są wartościami, które funkcja oczekuje odbierania. Prototypu funkcji nawiasów po nazwie funkcji zawiera pełną listę parametrów funkcji i ich typy. Deklaracji parametrów określić typy, rozmiary i identyfikatory wartości przechowywane w parametrach.

## <a name="syntax"></a>Składnia

*Definicja funkcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub> *atrybutu seq*<sub>zoptymalizowany pod kątem</sub> *deklaratora* *lista deklaracji*  <sub>zoptymalizowany pod kątem</sub> *compound-statement*

/\* *Atrybut seq* jest Specific dla Microsoft \*/

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wskaźnik*<sub>zoptymalizowany pod kątem</sub> *deklaratora bezpośrednie*

*deklarator bezpośrednio*: /\* deklaratora funkcji \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy parametrów typu* **)**  / \* deklaratora nowy styl \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy identyfikatorów*<sub>zoptymalizowany pod kątem</sub> **)**  / \* Obsolete stylu deklarator \*/

*listy parametrów typu*: /\* listy parametrów \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **, ...**

*parameter-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,**  *parameter-declaration*

*parameter-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji* *deklaratora*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji* *abstrakcyjny declarator*<sub>zoptymalizowany pod kątem</sub>

*Listy parametrów typu* jest sekwencją deklaracji parametru rozdzielonych przecinkami. Formularz każdego parametru na liście parametrów wygląda następująco:

```C
[register]  type-specifier [declarator]
```

Parametry funkcji zadeklarowanych za pomocą **automatycznie** atrybut generować błędy. Identyfikatory parametry są używane w treści funkcji do odwoływania się do wartości przekazana do funkcji. Możesz nazwać parametrów prototypu, ale nazwy wykraczają poza zakres, na końcu deklaracji. W związku z tym nazwy parametru może mieć przypisany taki sam sposób lub w inny sposób w definicji funkcji. Nie można przedefiniować tych identyfikatorów w najbardziej zewnętrznej bloku treści funkcji, ale można je w blokach wewnętrznej, zagnieżdżonej tak, jakby lista parametrów była otaczającym bloku.

Każdy identyfikator w *listy parametrów typu* muszą być poprzedzone jego specyfikator odpowiedniego typu, jak pokazano w poniższym przykładzie:

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

Jeśli co najmniej jeden parametr występuje na liście parametrów, listy może kończyć się przecinkami następują trzy kropki (**,...** ). Tej konstrukcji, o nazwie "notacji wielokropka" wskazuje zmienną liczbę argumentów funkcji. (Zobacz [wywołania ze zmienną liczbą argumentów](../c-language/calls-with-a-variable-number-of-arguments.md) Aby uzyskać więcej informacji.) Jednak wywołanie funkcji musi mieć przynajmniej tyle argumentów są parametry przed ostatnim przecinkiem.

Jeśli żadne argumenty do przekazania do funkcji, lista parametrów zastępuje słowo kluczowe `void`. Użycie tego `void` różni się od jego użycie jako Specyfikator typu.

Kolejność i typ parametrów, łącznie z jakimkolwiek użyciem Notacja wielokropka musi być taka sama w wszystkie deklaracje funkcji (jeśli istnieje) i definicji funkcji. Typy argumentów po zwykle konwersje arytmetyczne musi być zgodny z przypisania z typami odpowiednich parametrów. (Zobacz [zwykle konwersje arytmetyczne](../c-language/usual-arithmetic-conversions.md) dotyczące konwersje arytmetyczne.) Argumenty następujące wielokropka nie są sprawdzane. Parametr może mieć żadnych podstawowego, struktury, złożenia, wskaźnikiem, lub typu tablicy.

Kompilator niezależnie wykonuje zwykle konwersje arytmetyczne dla każdego parametru i dla każdego argumentu, jeśli to konieczne. Po konwersji nie parametrze jest krótszy niż `int`, a nie parametrze ma **float** typu, chyba że typ parametru jest jawnie określona jako **float** w prototypie. Oznacza to, na przykład deklarowania jako parametru `char` ma taki sam skutek jak deklarowania go jako `int`.

## <a name="see-also"></a>Zobacz także

[Definicje funkcji języka C](../c-language/c-function-definitions.md)

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
- ellipsis (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
ms.openlocfilehash: 57648747bbb50ffe46b199a03563757c331f088a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229574"
---
# <a name="parameters"></a>Parametry

Argumenty są nazwami wartości przekazaną do funkcji przez wywołanie funkcji. Parametry są wartościami, które funkcja oczekuje na odebranie. W prototypie funkcji nawiasy po nazwie funkcji zawierają pełną listę parametrów funkcji i ich typów. Deklaracje parametrów określają typy, rozmiary i identyfikatory wartości przechowywanych w parametrach.

## <a name="syntax"></a>Składnia

*`function-definition`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`*<sub>wybór</sub> *`attribute-seq`* <sub>wybór</sub> *`declarator`* *`declaration-list`* <sub>wybór</sub>*`compound-statement`*

/\**`attribute-seq`* czy specyficzny dla firmy Microsoft\*/

*`declarator`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`pointer`*<sub>wybór</sub>*`direct-declarator`*

*`direct-declarator`*:/ \* Funkcja deklarator\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`direct-declarator`*  **`(`**  *`parameter-type-list`*  **`)`** /\*Deklarator nowego stylu\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`direct-declarator`*  **`(`**  *`identifier-list`*<sub>opt</sub> **`)`**  / wybór \* Przestarzałe style deklarator\*/

*`parameter-type-list`*:/ \* Lista parametrów\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`parameter-list`* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`parameter-list`* **`, ...`**

*`parameter-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`parameter-declaration`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`parameter-list`* **`,`**  *`parameter-declaration`*

*`parameter-declaration`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`* *`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`**`abstract-declarator`* <sub>wybór</sub>

*`parameter-type-list`* Jest sekwencją deklaracji parametrów oddzielonych przecinkami. Formularz każdego parametru na liście parametrów wygląda następująco:

> **`register`**<sub>wybór</sub> *`type-specifier`* *`declarator`* <sub>wybór</sub>

Parametry funkcji zadeklarowane za pomocą **`auto`** atrybutu generują błędy. Identyfikatory parametrów są używane w treści funkcji w celu odwoływania się do wartości przekazaną do funkcji. Parametry można nazwać w prototypie, ale nazwy wykraczają poza zakres na końcu deklaracji. Oznacza to, że nazwy parametrów mogą być przypisywane w taki sam sposób lub w różny sposób w definicji funkcji. Tych identyfikatorów nie można ponownie zdefiniować w zewnętrznym bloku treści funkcji, ale można je ponownie zdefiniować w wewnętrznych, zagnieżdżonych blokach tak, jakby lista parametrów była otaczającym blokiem.

Każdy identyfikator w *`parameter-type-list`* musi być poprzedzony odpowiadającym mu specyfikatorem typu, jak pokazano w poniższym przykładzie:

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

Jeśli na liście parametrów występuje co najmniej jeden parametr, lista może kończyć się przecinkiem, po którym następuje trzy kropki ( **`, ...`** ). Ta konstrukcja, nazywana "notacją wielokropka," oznacza zmienną liczbę argumentów funkcji. (Aby uzyskać więcej informacji, zobacz [wywołania z zmienną liczbą argumentów](../c-language/calls-with-a-variable-number-of-arguments.md)). Jednak wywołanie funkcji musi mieć co najmniej tyle argumentów, ponieważ istnieją parametry przed ostatnim przecinkiem.

Jeśli żadne argumenty nie mają być przekazane do funkcji, lista parametrów jest zastępowana słowem kluczowym **`void`** . To użycie **`void`** jest odrębne od jego użycia jako specyfikatora typu.

Kolejność i typ parametrów, łącznie z dowolnym użyciem notacji wielokropka, muszą być takie same we wszystkich deklaracjach funkcji (jeśli istnieją) i w definicji funkcji. Typy argumentów po zwykłych konwersje arytmetyczne muszą być zgodne z typami odpowiednich parametrów. (Zobacz [typowe konwersje arytmetyczne](../c-language/usual-arithmetic-conversions.md) , aby uzyskać informacje na temat konwersji arytmetycznych). Argumenty po wielokropku nie są zaznaczone. Parametr może mieć dowolny typ podstawowy, struktura, Unia, wskaźnik lub tablicę.

Kompilator wykonuje Zwykłe konwersje arytmetyczne niezależnie od każdego parametru i każdego argumentu, w razie potrzeby. Po konwersji żaden parametr nie jest krótszy niż **`int`** , a żaden parametr nie ma **`float`** typu, chyba że typ parametru jest jawnie określony jako **`float`** w prototypie. Oznacza to, na przykład, który deklaruje parametr jako **`char`** ma taki sam skutek jak zadeklarowanie go jako **`int`** .

## <a name="see-also"></a>Zobacz także

[Definicje funkcji języka C](../c-language/c-function-definitions.md)

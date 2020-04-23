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
ms.openlocfilehash: 78ad91ea86d81a3b6d888335ba7b78399a1d2aea
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032073"
---
# <a name="parameters"></a>Parametry

Argumenty są nazwami wartości przekazanych do funkcji przez wywołanie funkcji. Parametry są wartościami, które funkcja oczekuje. W prototypie funkcji nawiasy następujące po nazwie funkcji zawierają pełną listę parametrów funkcji i ich typów. Deklaracje parametrów określają typy, rozmiary i identyfikatory wartości przechowywanych w parametrach.

## <a name="syntax"></a>Składnia

*definicja funkcji:*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracja-specyfikatory*<sub>opt</sub> *atrybut-seq*<sub>opt</sub> *deklaracja-lista* *declaration-list*<sub>opt</sub> *złożone oświadczenie*

/\**attribute-seq* jest specyficzne dla firmy Microsoft\*/

*deklarator:*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wskaźnik*<sub>opt</sub> *bezpośredni deklarator*

*dekluzyjnik bezpośredni*: /\* Deklarator funkcji\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator***(***parameter-type-list***)**  / \* Nowy styl deklaratora      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator**(identyfikator-lista***(** / \* <sub>opt</sub> **opt)** Przestarzały deklarator    \*/

*lista parametrów typu*\* : / Lista parametrów\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*lista parametrów* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*lista parametrów* **, ...**

*lista parametrów:*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracja parametrów*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*lista parametrów* **,**  *deklaracja parametrów*

*deklaracja parametrów:*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarzy deklaracji* *declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracja-specyfikatory* *abstrakcyjne-deklarator*<sub>opt</sub>

*Lista typów parametrów* jest sekwencją deklaracji parametrów oddzielonych przecinkami. Forma każdego parametru na liście parametrów wygląda następująco:

```C
[register]  type-specifier [declarator]
```

Parametry funkcji zadeklarowane za pomocą atrybutu **auto** generują błędy. Identyfikatory parametrów są używane w treści funkcji w celu odwoływania się do wartości przekazanych do funkcji. Można nazwać parametry w prototypie, ale nazwy wykraczają poza zakres na końcu deklaracji. W związku z tym nazwy parametrów można przypisać w ten sam sposób lub inaczej w definicji funkcji. Identyfikatory te nie mogą być ponownie zdefiniowane w najbardziej zewnętrznym bloku treści funkcji, ale można je ponownie zdefiniować w wewnętrznych, zagnieżdżonych blokach tak, jakby lista parametrów była blokiem otaczającym.

Każdy identyfikator na *liście typów parametrów* musi być poprzedzony odpowiednim specyfikatorem typu, jak pokazano w tym przykładzie:

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

Jeśli na liście parametrów występuje co najmniej jeden parametr, lista może zakończyć się przecinkiem, po którym następuje trzy okresy (**, ...**). Ta konstrukcja, zwana "notacją wielokropek", wskazuje zmienną liczbę argumentów funkcji. (Aby uzyskać więcej informacji, zobacz [wywołania ze zmienną liczbą argumentów).](../c-language/calls-with-a-variable-number-of-arguments.md) Jednak wywołanie funkcji musi mieć co najmniej tyle argumentów, ile istnieją parametry przed ostatnim przecinkiem.

Jeśli do funkcji nie zostaną przekazane żadne argumenty, lista parametrów zostanie zastąpiona słowem kluczowym `void`. To użycie `void` różni się od jego użycia jako specyfikatora typu.

Kolejność i typ parametrów, w tym wszelkie użycie notacji wielokropka, musi być taka sama we wszystkich deklaracjach funkcji (jeśli istnieją) i w definicji funkcji. Typy argumentów po zwykłych konwersjach arytmetycznych muszą być zgodne z typami odpowiednich parametrów. (Zobacz [zwykłe konwersje arytmetyczne,](../c-language/usual-arithmetic-conversions.md) aby uzyskać informacje na temat konwersji arytmetycznych). Argumenty następujące po wielokropku nie są sprawdzane. Parametr może mieć dowolny typ podstawowy, struktura, związek, wskaźnik lub typ tablicy.

Kompilator wykonuje zwykłe konwersje arytmetyczne niezależnie od każdego parametru i każdego argumentu, jeśli to konieczne. Po konwersji żaden parametr `int`nie jest krótszy niż parametr , a żaden parametr nie ma typu **float,** chyba że typ parametru jest jawnie określony jako **float** w prototypie. Oznacza to na przykład, że deklarowanie `char` parametru jako parametru ma `int`taki sam skutek jak deklarowanie go jako .

## <a name="see-also"></a>Zobacz też

[Definicje funkcji języka C](../c-language/c-function-definitions.md)

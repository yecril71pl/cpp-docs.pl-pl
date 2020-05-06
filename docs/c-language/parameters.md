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

Argumenty są nazwami wartości przekazaną do funkcji przez wywołanie funkcji. Parametry są wartościami, które funkcja oczekuje na odebranie. W prototypie funkcji nawiasy po nazwie funkcji zawierają pełną listę parametrów funkcji i ich typów. Deklaracje parametrów określają typy, rozmiary i identyfikatory wartości przechowywanych w parametrach.

## <a name="syntax"></a>Składnia

*definicja funkcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja-specyfikators*<sub>opt</sub> *Attribute-SEQ*<sub>opt</sub> *deklarator* *deklaracji-list*<sub>opt</sub> *złożone-instrukcja*

/\**atrybut-seq* jest specyficzny dla firmy Microsoft\*/

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>wybór</sub> wskaźnika *Direct-deklarator*

*Direct-deklarator*:/\* A funkcja deklarator\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator***(***Typ parametru-list***)**  / \* New-Style deklarator      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator***(** nieważność*listy identyfikatorów*<sub>opt</sub> **)**  / \* — przestarzałe style deklarator    \*/

*Typ parametru-list*:/\* lista parametrów\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* **,...**

*Lista parametrów*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* **,**  *Deklaracja parametru*

*Deklaracja parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specyfikatory deklaracji* *deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;abstrakcyjne *specyfikatory deklaracji* *-deklarator*<sub>opt</sub>

*Typ parametru-list* jest sekwencją deklaracji parametrów oddzielonych przecinkami. Formularz każdego parametru na liście parametrów wygląda następująco:

```C
[register]  type-specifier [declarator]
```

Parametry funkcji zadeklarowane z **błędami generowania atrybutu** AutoGenerate. Identyfikatory parametrów są używane w treści funkcji w celu odwoływania się do wartości przekazaną do funkcji. Parametry można nazwać w prototypie, ale nazwy wykraczają poza zakres na końcu deklaracji. W związku z tym nazwy parametrów mogą być przypisywane w taki sam sposób lub w inny sposób w definicji funkcji. Tych identyfikatorów nie można ponownie zdefiniować w zewnętrznym bloku treści funkcji, ale można je ponownie zdefiniować w wewnętrznych, zagnieżdżonych blokach tak, jakby lista parametrów była otaczającym blokiem.

Każdy identyfikator na *liście parametrów typu* musi być poprzedzony odpowiednim specyfikatorem typu, jak pokazano w tym przykładzie:

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

Jeśli na liście parametrów występuje co najmniej jeden parametr, lista może kończyć się przecinkiem, po którym następuje trzy kropki (**,...**). Ta konstrukcja, nazywana "notacją wielokropka," oznacza zmienną liczbę argumentów funkcji. (Zobacz [wywołania z zmienną liczbą argumentów,](../c-language/calls-with-a-variable-number-of-arguments.md) Aby uzyskać więcej informacji). Jednak wywołanie funkcji musi mieć co najmniej tyle argumentów, ponieważ istnieją parametry przed ostatnim przecinkiem.

Jeśli żadne argumenty nie mają być przekazane do funkcji, lista parametrów jest zastępowana słowem kluczowym `void`. To użycie `void` jest odrębne od jego użycia jako specyfikatora typu.

Kolejność i typ parametrów, łącznie z dowolnym użyciem notacji wielokropka, muszą być takie same we wszystkich deklaracjach funkcji (jeśli istnieją) i w definicji funkcji. Typy argumentów po zwykłych konwersje arytmetyczne muszą być zgodne z typami odpowiednich parametrów. (Zobacz [typowe konwersje arytmetyczne](../c-language/usual-arithmetic-conversions.md) , aby uzyskać informacje na temat konwersji arytmetycznych). Argumenty po wielokropku nie są sprawdzane. Parametr może mieć dowolny typ podstawowy, struktura, Unia, wskaźnik lub tablicę.

Kompilator wykonuje Zwykłe konwersje arytmetyczne niezależnie od każdego parametru i każdego argumentu, w razie potrzeby. Po konwersji żaden parametr nie jest krótszy niż `int`, a żaden parametr nie ma typu **zmiennoprzecinkowego** , chyba że typ parametru jest jawnie określony jako **float** w prototypie. Oznacza to, na przykład, który deklaruje parametr jako `char` ma taki sam skutek jak zadeklarowanie go jako. `int`

## <a name="see-also"></a>Zobacz też

[Definicje funkcji języka C](../c-language/c-function-definitions.md)

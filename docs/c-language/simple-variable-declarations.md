---
title: Proste deklaracje zmiennej
ms.date: 11/04/2016
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
ms.openlocfilehash: 42547828e78566982053d22e8288fe1ccbe6e26b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229535"
---
# <a name="simple-variable-declarations"></a>Proste deklaracje zmiennej

Deklaracja zmiennej prostej, najprostsza forma deklarator bezpośredniego, określa nazwę i typ zmiennej. Określa również klasę magazynu i typ danych zmiennej.

Klasy lub typy magazynów (lub oba) są wymagane w deklaracjach zmiennych. Zmienne nietypu (takie jak `var;` ) generują ostrzeżenia.

## <a name="syntax"></a>Składnia

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>wybór</sub> wskaźnika *Direct-deklarator*

*deklarator Direct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatora*

*Identyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dowolny*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *niecyfrowy* identyfikator<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *cyfra* identyfikatora

W przypadku arytmetycznego, struktury, Unii, wyliczeń i typów void oraz dla typów reprezentowanych przez **`typedef`** nazwy, proste deklaratory może być używane w deklaracji, ponieważ specyfikator typu dostarcza wszystkie informacje o wpisywaniu. Typy wskaźników, tablic i funkcji wymagają bardziej skomplikowanej Deklaratory.

Możesz użyć listy identyfikatorów rozdzielonych przecinkami (**,),** aby określić kilka zmiennych w tej samej deklaracji. Wszystkie zmienne zdefiniowane w deklaracji mają ten sam typ podstawowy. Na przykład:

```C
int x, y;        /* Declares two simple variables of type int */
int const z = 1; /* Declares a constant value of type int */
```

Zmienne `x` i `y` mogą zawierać dowolną wartość w zestawie zdefiniowanym przez **`int`** Typ dla konkretnej implementacji. Obiekt prosty `z` jest inicjowany do wartości 1 i nie można go modyfikować.

Jeśli deklaracja `z` była dla niezainicjowanej zmiennej statycznej lub była w zakresie pliku, otrzyma wartość początkową 0 i nie można jej modyfikować.

```C
unsigned long reply, flag; /* Declares two variables
                              named reply and flag     */
```

W tym przykładzie zarówno zmienne, `reply` jak i `flag` mają **`unsigned long`** Typ i muszą zawierać niepodpisane wartości całkowite.

## <a name="see-also"></a>Zobacz także

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)

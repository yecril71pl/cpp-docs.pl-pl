---
title: Proste deklaracje zmiennej
ms.date: 11/04/2016
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
ms.openlocfilehash: 27710dabe512332564ee557a9d022457d9fddc5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158239"
---
# <a name="simple-variable-declarations"></a>Proste deklaracje zmiennej

Deklaracja zmiennej prostej, najprostsza forma deklarator bezpośredniego, określa nazwę i typ zmiennej. Określa również klasę magazynu i typ danych zmiennej.

Klasy lub typy magazynów (lub oba) są wymagane w deklaracjach zmiennych. Zmienne nietypu (takie jak `var;`) generują ostrzeżenia.

## <a name="syntax"></a>Składnia

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>wybór</sub> wskaźnika *Direct-deklarator*

*deklarator Direct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatora*

*Identyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dowolny*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *niecyfrowy* identyfikator<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *cyfra* identyfikatora

W przypadku arytmetycznego, struktury, Unii, wyliczeń i typów void oraz dla typów reprezentowanych przez `typedef` nazwy, proste deklaratory może być używane w deklaracji, ponieważ specyfikator typu dostarcza wszystkie informacje o wpisywaniu. Typy wskaźników, tablic i funkcji wymagają bardziej skomplikowanej Deklaratory.

Możesz użyć listy identyfikatorów rozdzielonych przecinkami (**,),** aby określić kilka zmiennych w tej samej deklaracji. Wszystkie zmienne zdefiniowane w deklaracji mają ten sam typ podstawowy. Przykład:

```C
int x, y;        /* Declares two simple variables of type int */
int const z = 1; /* Declares a constant value of type int */
```

Zmienne `x` i `y` mogą zawierać dowolną wartość w zestawie zdefiniowanym przez `int` typ dla konkretnej implementacji. Obiekt `z` prosty jest inicjowany do wartości 1 i nie można go modyfikować.

Jeśli deklaracja `z` była dla niezainicjowanej zmiennej statycznej lub była w zakresie pliku, otrzyma wartość początkową 0 i nie można jej modyfikować.

```C
unsigned long reply, flag; /* Declares two variables
                              named reply and flag     */
```

W tym przykładzie zarówno zmienne, `reply` jak i `flag`mają typ i `unsigned long` muszą zawierać niepodpisane wartości całkowite.

## <a name="see-also"></a>Zobacz też

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)

---
title: Proste deklaracje zmiennej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7216a4a470b6293a31d6f364626188e41351b5cb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763142"
---
# <a name="simple-variable-declarations"></a>Proste deklaracje zmiennej

Deklaracja zmiennej prosty, Najprostszą formą deklaratora bezpośrednich, określa nazwę i typ zmiennej. Określa również klasę magazynu w zmiennej i typ danych.

Klasy magazynu lub typów (lub obie) są wymagane w deklaracji zmiennej. Bez typu zmienne (takie jak `var;`) generowanie ostrzeżenia.

## <a name="syntax"></a>Składnia

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wskaźnik*<sub>zoptymalizowany pod kątem</sub> *deklaratora bezpośrednie*

*deklarator bezpośrednio*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*Identyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inny*<br/>
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

## <a name="see-also"></a>Zobacz też

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)
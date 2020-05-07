---
title: Przestarzałe formy deklaracji i definicji funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- old style function declarations
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
ms.openlocfilehash: f26e79a586ea451cc51b339b5be593c2359e1f1a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745871"
---
# <a name="obsolete-forms-of-function-declarations-and-definitions"></a>Przestarzałe formy deklaracji i definicji funkcji

Deklaracje i definicje funkcji starego stylu używają nieco różnych reguł deklarujących parametry niż składnia zalecana przez standard ANSI C. Najpierw deklaracje starych stylów nie mają listy parametrów. Po drugie, w definicji funkcji, parametry są wyświetlane, ale ich typy nie są zadeklarowane na liście parametrów. Deklaracje typu poprzedzają złożone instrukcje tworzące treść funkcji. Składnia starego stylu jest przestarzała i nie powinna być używana w nowym kodzie. Kod korzystający ze składni starego stylu jest jednak nadal obsługiwany. Ten przykład ilustruje przestarzałe formy deklaracji i definicji:

```
double old_style();           /* Obsolete function declaration */

double alt_style( a , real )  /* Obsolete function definition */
    double *real;
    int a;
{
    return ( *real + a ) ;
}
```

Funkcje zwracają liczbę całkowitą lub wskaźnik o takim samym rozmiarze, co `int` nie jest wymagane do posiadania deklaracji, chociaż jest zalecana deklaracja.

Aby zapewnić zgodność ze standardami ANSI C, deklaracje funkcji starego stylu przy użyciu wielokropka teraz generują błąd podczas kompilowania z opcją/za oraz ostrzeżenie poziomu 4 podczas kompilowania z/ze. Przykład:

```cpp
void funct1( a, ... )  /* Generates a warning under /Ze or */
int a;                 /* an error when compiling with /Za */
{
}
```

Należy ponownie napisać tę deklarację jako prototyp:

```cpp
void funct1( int a, ... )
{
}
```

Deklaracje funkcji starego stylu również generują ostrzeżenia, jeśli następnie deklarujesz lub zdefiniujesz tę samą funkcję z wielokropkiem lub parametrem typu, który nie jest taki sam jak jego podwyższony typ.

Następna sekcja, [definicje funkcji języka C](../c-language/c-function-definitions.md), pokazuje składnię definicji funkcji, w tym składnię starego stylu. Nieterminali dla listy parametrów w składni starego stylu to *Lista identyfikatorów*.

## <a name="see-also"></a>Zobacz też

[Przegląd funkcji](../c-language/overview-of-functions.md)

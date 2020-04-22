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

Deklaracje i definicje funkcji starego stylu używają nieco innych reguł deklarowania parametrów niż składnia zalecana przez normę ANSI C. Po pierwsze, deklaracje starego stylu nie mają listy parametrów. Po drugie, w definicji funkcji parametry są wyświetlane, ale ich typy nie są zadeklarowane na liście parametrów. Deklaracje typu poprzedzają instrukcję złożoną stanowiącą treść funkcji. Składnia starego stylu jest przestarzała i nie powinna być używana w nowym kodzie. Kod przy użyciu składni starego stylu jest nadal obsługiwane, jednak. W tym przykładzie przedstawiono przestarzałe formy deklaracji i definicji:

```
double old_style();           /* Obsolete function declaration */

double alt_style( a , real )  /* Obsolete function definition */
    double *real;
    int a;
{
    return ( *real + a ) ;
}
```

Funkcje zwracające całkowitą lub wskaźnik o tym `int` samym rozmiarze co deklaracja nie muszą mieć deklaracji, mimo że deklaracja jest zalecana.

Aby zapewnić zgodność ze standardem ANSI C, deklaracje funkcji starego stylu przy użyciu wielokropek generują teraz błąd podczas kompilowania z opcją /Za i ostrzeżeniem poziomu 4 podczas kompilowania z /Ze. Przykład:

```cpp
void funct1( a, ... )  /* Generates a warning under /Ze or */
int a;                 /* an error when compiling with /Za */
{
}
```

Należy przepisać tę deklarację jako prototyp:

```cpp
void funct1( int a, ... )
{
}
```

Deklaracje funkcji starego stylu również generować ostrzeżenia, jeśli następnie zadeklarować lub zdefiniować tę samą funkcję z wielokropka lub parametr z typem, który nie jest taki sam jak jego typu promowanego.

W następnej sekcji [definicje funkcji C](../c-language/c-function-definitions.md)przedstawiono składnię definicji funkcji, w tym składnię starego stylu. Nieterminowa dla listy parametrów w starej składni jest *lista identyfikatorów*.

## <a name="see-also"></a>Zobacz też

[Przegląd funkcji](../c-language/overview-of-functions.md)

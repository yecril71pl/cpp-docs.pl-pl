---
title: Przestarzałe formy deklaracji i definicji funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- old style function declarations
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
ms.openlocfilehash: 4822ee75c9a1112aff7c7b54dffb745325f56001
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444242"
---
# <a name="obsolete-forms-of-function-declarations-and-definitions"></a>Przestarzałe formy deklaracji i definicji funkcji

Definicje i deklaracje funkcji w starym stylu na użytek nieco inne reguły deklarowania parametrów niż składni, zaleca się przez standard ANSI C. Po pierwsze deklaracje stary styl nie ma listy parametrów. Po drugie w definicji funkcji parametry są wyświetlane, ale ich typy nie są zadeklarowane na liście parametrów. Deklaracje typu poprzedzać złożone wyrażenie tworzące treści funkcji. Składnia stary styl jest przestarzała i nie należy używać w nowym kodzie. Przy użyciu składni w starym stylu kodu jest nadal obsługiwany, jednak. Ten przykład ilustruje przestarzałe formy deklaracji i definicji:

```
double old_style();           /* Obsolete function declaration */

double alt_style( a , real )  /* Obsolete function definition */
    double *real;
    int a;
{
    return ( *real + a ) ;
}
```

Funkcji zwracających liczbą całkowitą lub wskaźnik o tym samym rozmiarze co `int` nie muszą mieć deklarację, mimo że deklaracja jest zalecane.

Do zapewnienia zgodności ze standardem ANSI C, deklaracje funkcji w starym stylu, przy użyciu wielokropka teraz generuje błąd, podczas kompilowania z opcją/za i poziom 4 ostrzeżenia podczas kompilowania za pomocą /Ze. Na przykład:

```
void funct1( a, ... )  /* Generates a warning under /Ze or */
int a;                 /* an error when compiling with /Za */
{
}
```

Znajdziesz tej deklaracji jako prototyp:

```
void funct1( int a, ... )
{
}
```

Deklaracje funkcji w starym stylu również generować ostrzeżenia, jeśli później zadeklarować lub zdefiniować tę samą funkcję wielokropkiem albo lub parametrem typu, który nie jest taka sama jak jego typ o podwyższonym poziomie.

Następnej sekcji [definicje funkcji języka C](../c-language/c-function-definitions.md), pokazuje składnię dla definicji funkcji, składni w starym stylu. Jest nieterminalnych, aby uzyskać listę parametrów w składni w starym stylu *listy identyfikatorów*.

## <a name="see-also"></a>Zobacz też

[Przegląd funkcji](../c-language/overview-of-functions.md)
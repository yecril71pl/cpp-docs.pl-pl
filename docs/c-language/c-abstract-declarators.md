---
title: Deklaratory abstrakcyjne języka C
ms.date: 11/04/2016
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
ms.openlocfilehash: f2ca0f4a367abf939ed4307611517a883d8b82e0
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152667"
---
# <a name="c-abstract-declarators"></a>Deklaratory abstrakcyjne języka C

Deklarator abstrakcji jest deklaratorów bez identyfikatora składający się z co najmniej jeden wskaźnik, tablicy lub funkcji modyfikatorów. Modyfikator wskaźnika (<strong>\*</strong>) zawsze poprzedza identyfikator w deklaratorze; tablicy (**[**) i funkcji ( **()** ) Modyfikatory postępuj zgodnie z identyfikatorem. Wiedza o tym, można określić, gdzie pojawiają się w abstrakcyjnym deklaratorze i interpretować deklaratora w związku z tym identyfikatorem. Zobacz [interpretowanie bardziej Deklaratorów złożonych](../c-language/interpreting-more-complex-declarators.md) dodatkowe informacje i przykłady deklaratorów złożonych. Ogólnie `typedef` można uproszczenie deklaratorów. Zobacz [deklaracje Typedef](../c-language/typedef-declarations.md).

Deklaratory abstrakcyjne mogą być skomplikowane. Nawiasy w złożonych abstrakcyjnym deklaratorze Określ określonego interpretacji, tak jak w przypadku deklaratorów złożonych w deklaracji.

Te przykłady ilustrują deklaratory abstrakcyjne:

```
int *         // The type name for a pointer to type int:

int *[3]      // An array of three pointers to int

int (*) [5]   // A pointer to an array of five int

int *()       // A function with no parameter specification
              // returning a pointer to int

// A pointer to a function taking no arguments and
// returning an int

int (*) ( void )

// An array of an unspecified number of constant pointers to
// functions each with one parameter that has type unsigned int
// and an unspecified number of other parameters returning an int

int (*const []) ( unsigned int, ... )
```

> [!NOTE]
>  Abstrakcyjnym deklaratorze zawierający zestaw pustych nawiasów **()**, nie jest dozwolone, ponieważ jest ona niejednoznaczna. Jest to niemożliwe do należy określić, czy identyfikator dorozumianych należy w nawiasach (w takim przypadku jest typem niezmodyfikowanego) lub przed nawiasy (w takim przypadku jest typem funkcji).

## <a name="see-also"></a>Zobacz także

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)

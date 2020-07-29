---
title: Deklaratory abstrakcyjne języka C
ms.date: 11/04/2016
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
ms.openlocfilehash: 540b938e2c4121f189216942bc06630fc61ee19c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220863"
---
# <a name="c-abstract-declarators"></a>Deklaratory abstrakcyjne języka C

Abstrakcyjny deklarator to deklarator bez identyfikatora składający się z co najmniej jednego modyfikatora wskaźnika, tablicy lub funkcji. Modyfikator wskaźnika ( <strong>\*</strong> ) zawsze poprzedza identyfikator w modyfikatorze deklarator; Array (**[]**) i funkcji ( **()** ) podążać za identyfikatorem. Wiedząc, że identyfikator będzie widoczny w abstrakcyjnej deklarator i odpowiednio interpretuje deklarator. Zobacz [Interpretowanie bardziej złożonej Deklaratory](../c-language/interpreting-more-complex-declarators.md) , aby uzyskać dodatkowe informacje i przykłady złożonej Deklaratory. Zwykle **`typedef`** może służyć do uproszczenia Deklaratory. Zobacz [deklaracje typedef](../c-language/typedef-declarations.md).

Abstrakcyjny Deklaratory może być skomplikowany. Nawiasy w złożonej deklarator abstrakcyjnej określają konkretną interpretację, podobnie jak w przypadku złożonych Deklaratory w deklaracjach.

Przykłady te ilustrują abstrakcyjny Deklaratory:

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
> Abstrakcyjny deklarator składający się z zestawu pustych nawiasów **()** jest niedozwolony, ponieważ jest niejednoznaczny. Nie można ustalić, czy implikowany identyfikator należy do nawiasów (w którym przypadku jest to niemodyfikowany typ) czy przed nawiasami (w tym przypadku jest to typ funkcji).

## <a name="see-also"></a>Zobacz także

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)

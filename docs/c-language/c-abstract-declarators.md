---
title: Deklaratory abstrakcyjne języka C
ms.date: 11/04/2016
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
ms.openlocfilehash: 196eb39d901b38ab7b005b03a933827ec4288218
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335068"
---
# <a name="c-abstract-declarators"></a>Deklaratory abstrakcyjne języka C

Deklarator abstrakcyjny jest deklaratorem bez identyfikatora, składającym się z co najmniej jednego wskaźnika, tablicy lub modyfikatorów funkcji. Modyfikator wskaźnika (<strong>\*</strong>) zawsze poprzedza identyfikator w deklaratorze; modyfikatory tablicy (**[ ]**) i funkcji ( **( )** ) są zgodne z identyfikatorem. Wiedząc o tym, można określić, gdzie identyfikator pojawi się w deklaratorze abstrakcyjnym i odpowiednio zinterpretować deklaratora. Zobacz [interpretacji bardziej złożonych deklaratorów, aby](../c-language/interpreting-more-complex-declarators.md) uzyskać dodatkowe informacje i przykłady złożonych deklaratorów. Ogólnie `typedef` może służyć do uproszczenia deklaratorów. Zobacz [Deklaracje typedef](../c-language/typedef-declarations.md).

Abstrakcyjne deklaratory mogą być złożone. Nawiasy w złożonym deklaratorze abstrakcyjnym określają określoną interpretację, podobnie jak w przypadku złożonych deklaratorów w deklaracjach.

Przykłady te ilustrują abstrakcyjne deklaratory:

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
> Abstrakcyjny deklarator składający się z zestawu pustych nawiasów ( **)** nie jest dozwolony, ponieważ jest niejednoznaczny. Nie można ustalić, czy dorozumiany identyfikator należy do nawiasów (w którym to przypadku jest to typ niezmodyfikowany) lub przed nawiasami (w którym to przypadku jest to typ funkcji).

## <a name="see-also"></a>Zobacz też

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)

---
title: Deklaratory abstrakcyjne języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc89682a6d092bd5291551f01d9d592d64fdff85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381824"
---
# <a name="c-abstract-declarators"></a>Deklaratory abstrakcyjne języka C
Deklarator abstrakcyjnej jest deklaratorze bez identyfikatora składające się z co najmniej jednego wskaźnika, tablic lub funkcja modyfikatorów. Modyfikator wskaźnika (**\***) zawsze poprzedza identyfikator w deklaratorze; tablicy (**[**) i funkcji ( **()** ) Modyfikatory postępuj zgodnie z identyfikatorem. Wiedzy o to, można określić, gdzie identyfikator będzie wyświetlane w abstrakcyjnej deklarator i odpowiednio interpretowanie deklaratorów. Zobacz [interpretowanie więcej Deklaratorów złożonych](../c-language/interpreting-more-complex-declarators.md) dodatkowe informacje i przykłady deklaratorów złożonych. Ogólnie rzecz biorąc `typedef` może służyć do uproszczenia deklaratorów. Zobacz [deklaracje Typedef](../c-language/typedef-declarations.md).  
  
 Deklaratory abstrakcyjne języka może być skomplikowane. Nawiasów w złożonych deklarator abstrakcyjny Określ określonego interpretacji, podobnie jak w przypadku deklaratorów złożonych w deklaracjach.  
  
 Tych przykładach deklaratory abstrakcyjne języka:  
  
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
>  Deklarator abstrakcyjna, zawierający zestaw pustych nawiasów **()**, nie jest dozwolona, ponieważ jest ona niejednoznaczna. Nie można określić, czy identyfikator domyślnych należy wewnątrz nawiasów (w takim przypadku jest typem bez modyfikacji) lub przed nawiasów (w takim przypadku jest typem funkcji).  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)
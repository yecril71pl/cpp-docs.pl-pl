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
ms.openlocfilehash: ea9ca44dbc484749cc10a59fec0b91d096921827
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214535"
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
  
## <a name="see-also"></a>Zobacz też  
 [Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)
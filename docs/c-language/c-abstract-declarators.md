---
title: "Deklaratory abstrakcyjne języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e16711a61b3c8060396ce10aa2061600903499e
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
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
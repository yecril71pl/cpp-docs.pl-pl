---
title: Wyrażenie Statement (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18d28cdc695ae600616d63575328eeaf171bc28c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385900"
---
# <a name="expression-statement-c"></a>Instrukcja wyrażeń (C)
Po wykonaniu instrukcji wyrażenia wyrażenie jest obliczane zgodnie z regułami opisane w temacie [wyrażenia i przydziały](../c-language/expressions-and-assignments.md).  
  
## <a name="syntax"></a>Składnia  
 *Instrukcja wyrażeń*:  
 *wyrażenie* opt **;**  
  
 Przed wykonaniem następnej instrukcji, wykonywane są wszystkie efekty uboczne z Obliczanie wyrażenia. Instrukcja pusta wyrażenia jest nazywany instrukcja o wartości null. Zobacz [instrukcja o wartości Null](../c-language/null-statement-c.md) Aby uzyskać więcej informacji.  
  
 Poniższe przykłady pokazują wyrażeń.  
  
```  
x = ( y + 3 );            /* x is assigned the value of y + 3  */  
x++;                      /* x is incremented                  */  
x = y = 0;                /* Both x and y are initialized to 0 */  
proc( arg1, arg2 );       /* Function call returning void      */  
y = z = ( f( x ) + 3 );   /* A function-call expression        */  
```  
  
 Ostatnim wyrażenie wywołania funkcji wartości wyrażenia, zawierającą wartości zwracane przez funkcję wzrosła o 3 i przypisywana do obu zmiennych `y` i `z`.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje](../c-language/statements-c.md)
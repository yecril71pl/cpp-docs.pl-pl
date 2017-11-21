---
title: "Przegląd instrukcji C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: statements [C++]
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: be2836f095a6ec5d8861def985d4561eacd7b1f4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="overview-of-c-statements"></a>Przegląd instrukcji C++
Instrukcje C++ są wykonywane sekwencyjnie, z wyjątkiem przypadków, gdy instrukcja wyrażenia, instrukcja zaznaczenia, instrukcji iteracji lub instrukcji skok specjalnie modyfikuje tej sekwencji.  
  
 Instrukcje mogą być następujące:  
  
```  
  
labeled-statement  
expression-statement  
compound-statement  
selection-statement  
iteration-statement  
jump-statement  
declaration-statement  
try-throw-catch  
  
```  
  
 W większości przypadków jest identyczna jak c. ANSI C++ — składnia instrukcji Podstawowa różnica między nimi jest w języku C, deklaracje są dozwolone tylko na początku bloku; Dodaje C++ *instrukcji deklaracji*, którego usunięcie tego ograniczenia. Dzięki temu można wprowadzić zmiennych w punkcie w programie, w którym może zostać obliczona wartość wstępnie obliczonych inicjowania.  
  
 Deklarowanie zmiennych wewnątrz bloków umożliwia również wykonywanie ścisła kontrola nad zakresu i okresem istnienia tych zmiennych.  
  
 W tematach w instrukcjach opisano następujące słowa kluczowe języka C++:  
  
|||||  
|-|-|-|-|  
|[podział](../cpp/break-statement-cpp.md)|[else](../cpp/if-else-statement-cpp.md)|[__if_exists](../cpp/if-exists-statement.md)|[__try](../cpp/structured-exception-handling-c-cpp.md)|  
|[Case](../cpp/switch-statement-cpp.md)|[__except](../cpp/structured-exception-handling-c-cpp.md)|[__if_not_exists](../cpp/if-not-exists-statement.md)|[Spróbuj](../cpp/try-throw-and-catch-statements-cpp.md)|  
|[CATCH](../cpp/try-throw-and-catch-statements-cpp.md)|[dla](../cpp/for-statement-cpp.md)|[__leave](../c-language/try-finally-statement-c.md)|[Podczas](../cpp/while-statement-cpp.md)|  
|[Kontynuuj](../cpp/continue-statement-cpp.md)|[Przejdź do](../cpp/goto-statement-cpp.md)|[Zwraca](../cpp/return-statement-cpp.md)||  
|[domyślne](../cpp/switch-statement-cpp.md)|[__finally](../cpp/structured-exception-handling-c-cpp.md)|[Przełącznik](../cpp/switch-statement-cpp.md)||  
|[czy](../cpp/do-while-statement-cpp.md)|[Jeśli](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje](../cpp/statements-cpp.md)
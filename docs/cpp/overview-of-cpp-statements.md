---
title: Przegląd instrukcji C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements [C++]
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2858807816178115dd34c05d6c88c3dd6fecdee3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
|[break](../cpp/break-statement-cpp.md)|[else](../cpp/if-else-statement-cpp.md)|[__if_exists](../cpp/if-exists-statement.md)|[__try](../cpp/structured-exception-handling-c-cpp.md)|  
|[Case](../cpp/switch-statement-cpp.md)|[__except](../cpp/structured-exception-handling-c-cpp.md)|[__if_not_exists](../cpp/if-not-exists-statement.md)|[Spróbuj](../cpp/try-throw-and-catch-statements-cpp.md)|  
|[catch](../cpp/try-throw-and-catch-statements-cpp.md)|[for](../cpp/for-statement-cpp.md)|[__leave](../c-language/try-finally-statement-c.md)|[while](../cpp/while-statement-cpp.md)|  
|[continue](../cpp/continue-statement-cpp.md)|[goto](../cpp/goto-statement-cpp.md)|[return](../cpp/return-statement-cpp.md)||  
|[default](../cpp/switch-statement-cpp.md)|[__finally](../cpp/structured-exception-handling-c-cpp.md)|[switch](../cpp/switch-statement-cpp.md)||  
|[do](../cpp/do-while-statement-cpp.md)|[if](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje](../cpp/statements-cpp.md)
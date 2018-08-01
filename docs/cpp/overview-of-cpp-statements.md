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
ms.openlocfilehash: 426709857447d972365aa034059bcd34305d6d40
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402513"
---
# <a name="overview-of-c-statements"></a>Przegląd instrukcji C++
Instrukcje języka C++ są wykonywane sekwencyjnie, z wyjątkiem sytuacji, gdy instrukcja wyrażenia, instrukcja zaznaczenia, instrukcję iteracji lub instrukcja skoku specjalnie modyfikuje tej sekwencji.  
  
 Instrukcje mogą być następujących typów:  
  
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
  
 W większości przypadków składnia instrukcji języka C++ jest taka sama jak w przypadku standardu ANSI C. Główną różnicą między tymi dwoma jest to, że w języku C, deklaracji są dozwolone tylko na początku bloku; Dodaje C++ *instrukcji deklaracji*, które skutecznie powoduje usunięcie tego ograniczenia. Dzięki temu można wprowadzać zmiennych w punkcie, w programie, gdzie można obliczyć wartości wstępnie obliczonych inicjowania.  
  
 Deklarowanie zmiennych wewnątrz bloków umożliwia również wykonywać precyzyjną kontrolę nad zakresu i czasu życia tych zmiennych.  
  
 W tematach w instrukcjach opisano następujące słowa kluczowe języka C++:  
  
|||||  
|-|-|-|-|  
|[break](../cpp/break-statement-cpp.md)|[else](../cpp/if-else-statement-cpp.md)|[__if_exists —](../cpp/if-exists-statement.md)|[__try](../cpp/structured-exception-handling-c-cpp.md)|  
|[przypadek](../cpp/switch-statement-cpp.md)|[__except](../cpp/structured-exception-handling-c-cpp.md)|[__if_not_exists —](../cpp/if-not-exists-statement.md)|[Wypróbuj](../cpp/try-throw-and-catch-statements-cpp.md)|  
|[catch](../cpp/try-throw-and-catch-statements-cpp.md)|[for](../cpp/for-statement-cpp.md)|[__leave](../c-language/try-finally-statement-c.md)|[while](../cpp/while-statement-cpp.md)|  
|[continue](../cpp/continue-statement-cpp.md)|[goto](../cpp/goto-statement-cpp.md)|[return](../cpp/return-statement-cpp.md)||  
|[default](../cpp/switch-statement-cpp.md)|[__finally](../cpp/structured-exception-handling-c-cpp.md)|[switch](../cpp/switch-statement-cpp.md)||  
|[do](../cpp/do-while-statement-cpp.md)|[if](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje](../cpp/statements-cpp.md)
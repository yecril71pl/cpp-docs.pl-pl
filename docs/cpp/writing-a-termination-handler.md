---
title: Pisanie programu obsługi zakończenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], termination handlers
- exceptions [C++], terminating
- termination handlers [C++], writing
- handlers [C++]
- handlers [C++], termination
- termination handlers
- exception handling [C++], termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d37319e50e7d2429ca9b64c5fc81d8c7c4418ed5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="writing-a-termination-handler"></a>Pisanie programu obsługi zakończenia
W przeciwieństwie do obsługi wyjątków programu obsługi zakończenia jest zawsze wykonywane, niezależnie od tego, czy chroniony bloku kodu zakończone normalnie. Wyłącznie w celu obsługi rozwiązanie powinno być upewnij się, że zasoby, takie jak pamięć, dojść i plików, są prawidłowo zamknięty niezależnie od tego, jak sekcji kodu ukończeniem wykonywania.  
  
 Programy obsługi zakończenia używać instrukcji try-finally.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Try-finally — instrukcja](../cpp/try-finally-statement.md)  
  
-   [Oczyszczanie zasobów](../cpp/cleaning-up-resources.md)  
  
-   [Czas działania w obsłudze wyjątków](../cpp/timing-of-exception-handling-a-summary.md)  
  
-   [Ograniczenia dotyczące programu obsługi zakończenia](../cpp/restrictions-on-termination-handlers.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
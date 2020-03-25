---
title: Przegląd instrukcji C++
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++]
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
ms.openlocfilehash: 9aba5deddca6fbf480cd9d573606b16b7ab047db
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188431"
---
# <a name="overview-of-c-statements"></a>Przegląd instrukcji C++

C++instrukcje są wykonywane sekwencyjnie, z wyjątkiem sytuacji, gdy instrukcja wyrażenia, instrukcja SELECT, instrukcja iteracji lub instrukcja skoku modyfikują tę sekwencję.

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

W większości przypadków składnia C++ instrukcji jest taka sama jak w przypadku ANSI C. Główną różnicą między tymi dwiema jest to, że w C, deklaracje są dozwolone tylko na początku bloku; C++ dodaje *instrukcję deklaracji*, która skutecznie usuwa to ograniczenie. Pozwala to wprowadzić zmienne w punkcie w programie, w którym można obliczyć wstępnie obliczoną wartość inicjującą.

Deklarowanie zmiennych wewnątrz bloków pozwala na ścisłą kontrolę nad zakresem i okresem istnienia zmiennych.

Tematy dotyczące instrukcji opisują następujące C++ słowa kluczowe:

|||||
|-|-|-|-|
|[break](../cpp/break-statement-cpp.md)|[Przejmi](../cpp/if-else-statement-cpp.md)|[__if_exists](../cpp/if-exists-statement.md)|[__try](../cpp/structured-exception-handling-c-cpp.md)|
|[case](../cpp/switch-statement-cpp.md)|[__except](../cpp/structured-exception-handling-c-cpp.md)|[__if_not_exists](../cpp/if-not-exists-statement.md)|[spróbował](../cpp/try-throw-and-catch-statements-cpp.md)|
|[efektywn](../cpp/try-throw-and-catch-statements-cpp.md)|[for](../cpp/for-statement-cpp.md)|[__leave](../c-language/try-finally-statement-c.md)|[while](../cpp/while-statement-cpp.md)|
|[continue](../cpp/continue-statement-cpp.md)|[goto](../cpp/goto-statement-cpp.md)|[return](../cpp/return-statement-cpp.md)||
|[default](../cpp/switch-statement-cpp.md)|[__finally](../cpp/structured-exception-handling-c-cpp.md)|[switch](../cpp/switch-statement-cpp.md)||
|[do](../cpp/do-while-statement-cpp.md)|[przypadku](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||

## <a name="see-also"></a>Zobacz też

[Instrukcje](../cpp/statements-cpp.md)

---
title: Przegląd instrukcji C++
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++]
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
ms.openlocfilehash: 9493860087331ee2d8ff05a5c0bd59c7a46ad51a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325562"
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
|[break](../cpp/break-statement-cpp.md)|[else](../cpp/if-else-statement-cpp.md)|[__if_exists](../cpp/if-exists-statement.md)|[__try](../cpp/structured-exception-handling-c-cpp.md)|
|[case](../cpp/switch-statement-cpp.md)|[__except](../cpp/structured-exception-handling-c-cpp.md)|[__if_not_exists](../cpp/if-not-exists-statement.md)|[try](../cpp/try-throw-and-catch-statements-cpp.md)|
|[catch](../cpp/try-throw-and-catch-statements-cpp.md)|[for](../cpp/for-statement-cpp.md)|[__leave](../c-language/try-finally-statement-c.md)|[while](../cpp/while-statement-cpp.md)|
|[continue](../cpp/continue-statement-cpp.md)|[goto](../cpp/goto-statement-cpp.md)|[return](../cpp/return-statement-cpp.md)||
|[default](../cpp/switch-statement-cpp.md)|[__finally](../cpp/structured-exception-handling-c-cpp.md)|[switch](../cpp/switch-statement-cpp.md)||
|[do](../cpp/do-while-statement-cpp.md)|[if](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||

## <a name="see-also"></a>Zobacz także

[Instrukcje](../cpp/statements-cpp.md)
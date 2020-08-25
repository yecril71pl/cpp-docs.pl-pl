---
title: Przegląd instrukcji C++
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++]
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
ms.openlocfilehash: d6bd6b5bb7ba4b83fbed63a40fecc8194cb3707a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832428"
---
# <a name="overview-of-c-statements"></a>Przegląd instrukcji C++

Instrukcje języka C++ są wykonywane sekwencyjnie, z wyjątkiem sytuacji, gdy instrukcja wyrażenia, instrukcja SELECT, instrukcja iteracji lub instrukcja skoku modyfikują tę sekwencję.

Instrukcje mogą być następujące:

> *`labeled-statement`*\
> *`expression-statement`*\
> *`compound-statement`*\
> *`selection-statement`*\
> *`iteration-statement`*\
> *`jump-statement`*\
> *`declaration-statement`*\
> *`try-throw-catch`*

W większości przypadków składnia instrukcji C++ jest taka sama jak w przypadku ANSI c89. Podstawowa różnica między nimi polega na tym, że w C89 deklaracje są dozwolone tylko na początku bloku; C++ dodaje *`declaration-statement`* , które skutecznie usuwa to ograniczenie. Pozwala to wprowadzić zmienne w punkcie w programie, w którym można obliczyć wstępnie obliczoną wartość inicjującą.

Deklarowanie zmiennych wewnątrz bloków pozwala na ścisłą kontrolę nad zakresem i okresem istnienia zmiennych.

Artykuły na temat instrukcji opisują następujące słowa kluczowe języka C++:

:::row:::
   :::column span="":::
      [`break`](../cpp/break-statement-cpp.md)\
      [`case`](../cpp/switch-statement-cpp.md)\
      [`catch`](../cpp/try-throw-and-catch-statements-cpp.md)\
      [`continue`](../cpp/continue-statement-cpp.md)\
      [`default`](../cpp/switch-statement-cpp.md)\
      [`do`](../cpp/do-while-statement-cpp.md)
   :::column-end:::
   :::column span="":::
      [`else`](../cpp/if-else-statement-cpp.md)\
      [`__except`](../cpp/structured-exception-handling-c-cpp.md)\
      [`__finally`](../cpp/structured-exception-handling-c-cpp.md)\
      [`for`](../cpp/for-statement-cpp.md)\
      [`goto`](../cpp/goto-statement-cpp.md)
   :::column-end:::
   :::column span="":::
      [`if`](../cpp/if-else-statement-cpp.md)\
      [`__if_exists`](../cpp/if-exists-statement.md)\
      [`__if_not_exists`](../cpp/if-not-exists-statement.md)\
      [`__leave`](../c-language/try-finally-statement-c.md)\
      [`return`](../cpp/return-statement-cpp.md)
   :::column-end:::
   :::column span="":::
      [`switch`](../cpp/switch-statement-cpp.md)\
      [`throw`](../cpp/try-throw-and-catch-statements-cpp.md)\
      [`__try`](../cpp/structured-exception-handling-c-cpp.md)\
      [`try`](../cpp/try-throw-and-catch-statements-cpp.md)\
      [`while`](../cpp/while-statement-cpp.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Zobacz też

[Instrukcje](../cpp/statements-cpp.md)

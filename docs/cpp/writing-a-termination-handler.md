---
title: Pisanie programu obsługi zakończenia
ms.date: 11/04/2016
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
ms.openlocfilehash: f0b994075a8d59ce5d0955f10bf8c61d357d2db9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209471"
---
# <a name="writing-a-termination-handler"></a>Pisanie programu obsługi zakończenia

W przeciwieństwie do obsługi wyjątków programu obsługi zakończenia zawsze jest wykonywany w całości, niezależnie od tego, czy chroniony blok kodu zostało zakończone normalnie. Wyłącznie do celów programu obsługi zakończenia powinno być upewnij się, że zasoby, takie jak pamięć, obsługi i plików, są poprawnie zamknięte niezależnie od tego, jak sekcji kodu zakończy się wykonywanie.

Programy obsługi zakończenia użyj instrukcji try-finally.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Try-finally — instrukcja](../cpp/try-finally-statement.md)

- [Oczyszczanie zasobów](../cpp/cleaning-up-resources.md)

- [Czas działania w obsłudze wyjątków](../cpp/timing-of-exception-handling-a-summary.md)

- [Ograniczenia dotyczące programu obsługi zakończenia](../cpp/restrictions-on-termination-handlers.md)

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
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
ms.openlocfilehash: 8a243281e0d984a42cd4b4d9f249d867812d8bca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187313"
---
# <a name="writing-a-termination-handler"></a>Pisanie programu obsługi zakończenia

W przeciwieństwie do programu obsługi wyjątków, program obsługi zakończenia jest zawsze wykonywany, niezależnie od tego, czy chroniony blok kodu został zakończony normalnie. Jedynym celem programu obsługi zakończenia powinna być upewnienie się, że zasoby, takie jak pamięć, uchwyty i pliki, są prawidłowo zamknięte niezależnie od tego, jak sekcja kodu kończy wykonywanie.

Programy obsługi zakończenia używają instrukcji try-finally.

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Instrukcja try-finally](../cpp/try-finally-statement.md)

- [Czyszczenie zasobów](../cpp/cleaning-up-resources.md)

- [Chronometraż akcji w obsłudze wyjątków](../cpp/timing-of-exception-handling-a-summary.md)

- [Ograniczenia dotyczące obsługi zakończenia](../cpp/restrictions-on-termination-handlers.md)

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

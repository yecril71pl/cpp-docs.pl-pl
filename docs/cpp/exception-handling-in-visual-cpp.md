---
title: Obsługa wyjątków w MSVC
ms.date: 11/19/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 6cf71d6e6d0519951a084ebead65003bd363395f
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246594"
---
# <a name="exception-handling-in-msvc"></a>Obsługa wyjątków w MSVC

Wyjątek jest warunkiem błędu, możliwie poza kontrolą programu, który uniemożliwia kontynuowanie wykonywania programu wzdłuż zwykłej ścieżki. Niektóre operacje, w tym tworzenie obiektu, odczyt z/zapis do pliku i wywołania funkcji z innych modułów, są potencjalnymi źródłami wyjątków, nawet wtedy, gdy program działa poprawnie. Niezawodny kod przewiduje wyjątki i je obsługuje. Aby wykryć błędy logiki, użyj potwierdzeń zamiast wyjątków (zobacz [using Assertions](/visualstudio/debugger/c-cpp-assertions)).

## <a name="kinds-of-exceptions"></a>Rodzaje wyjątków

Kompilator firmy C++ Microsoft (MSVC) obsługuje trzy rodzaje obsługi wyjątków:

- [C++Obsługa wyjątków](errors-and-exception-handling-modern-cpp.md)

   W większości programów, należy używać obsługę wyjątków C++, co jest bezpieczne względem typu i zapewnia wywołanie destruktorów obiektów podczas wykonywania operacji odwijania stosu.

- [Strukturalna obsługa wyjątków](structured-exception-handling-c-cpp.md)

   System Windows zawiera własny mechanizm wyjątków, nazywany SEH. Nie zaleca się stosowania tego systemu w programowaniu C++ lub MFC. Używaj SEH tylko w programach innych niż MFC C.

- [Wyjątki MFC](../mfc/exception-handling-in-mfc.md)

Użyj opcji kompilatora [/EH](../build/reference/eh-exception-handling-model.md) , aby określić typ obsługi wyjątków, który ma być używany w projekcie; C++ obsługa wyjątków jest wartością domyślną. Nie należy mieszać mechanizmów obsługi błędów; na przykład nie należy używać C++ wyjątków z obsługą wyjątków strukturalnych. Korzystanie C++ z obsługi wyjątków sprawia, że kod jest bardziej przenośny i umożliwia obsługę wyjątków dowolnego typu. Aby uzyskać więcej informacji na temat wad obsługi wyjątków strukturalnych, zobacz [strukturalna obsługa wyjątków](structured-exception-handling-c-cpp.md). Aby uzyskać porady na temat mieszania makr C++ MFC i wyjątków, zobacz [wyjątki: używanie makr C++ MFC i wyjątków](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="in-this-section"></a>W tej sekcji

- [Nowoczesne C++ najlepsze rozwiązania dotyczące wyjątków i obsługi błędów](errors-and-exception-handling-modern-cpp.md)

- [Jak projektować pod kątem bezpieczeństwa wyjątków](how-to-design-for-exception-safety.md)

- [Jak interfejsować między wyjątkowym i niewyjątkowym kodem](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [Instrukcje try, catch i throw](try-throw-and-catch-statements-cpp.md)

- [Jak są obliczane bloki catch](how-catch-blocks-are-evaluated-cpp.md)

- [Wyjątki i odwracanie stosu](exceptions-and-stack-unwinding-in-cpp.md)

- [Specyfikacje wyjątków](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Nieobsługiwane wyjątki języka C++](unhandled-cpp-exceptions.md)

- [Połączenie wyjątków języka C (strukturalnych) i C++](mixing-c-structured-and-cpp-exceptions.md)

- [Obsługa wyjątków strukturalnych (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](cpp-language-reference.md)</br>
[Obsługa wyjątku x64](../build/exception-handling-x64.md)</br>
[Obsługa wyjątków (C++/CLI i C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)

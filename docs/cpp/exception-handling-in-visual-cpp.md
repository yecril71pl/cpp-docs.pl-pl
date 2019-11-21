---
title: Exception handling in MSVC
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
# <a name="exception-handling-in-msvc"></a>Exception handling in MSVC

Wyjątek jest warunkiem błędu, możliwie poza kontrolą programu, który uniemożliwia kontynuowanie wykonywania programu wzdłuż zwykłej ścieżki. Niektóre operacje, w tym tworzenie obiektu, odczyt z/zapis do pliku i wywołania funkcji z innych modułów, są potencjalnymi źródłami wyjątków, nawet wtedy, gdy program działa poprawnie. Niezawodny kod przewiduje wyjątki i je obsługuje. To detect logic errors, use assertions rather than exceptions (see [Using Assertions](/visualstudio/debugger/c-cpp-assertions)).

## <a name="kinds-of-exceptions"></a>Kinds of exceptions

The Microsoft C++ compiler (MSVC) supports three kinds of exception handling:

- [C++ exception handling](errors-and-exception-handling-modern-cpp.md)

   W większości programów, należy używać obsługę wyjątków C++, co jest bezpieczne względem typu i zapewnia wywołanie destruktorów obiektów podczas wykonywania operacji odwijania stosu.

- [Structured exception handling](structured-exception-handling-c-cpp.md)

   System Windows zawiera własny mechanizm wyjątków, nazywany SEH. Nie zaleca się stosowania tego systemu w programowaniu C++ lub MFC. Use SEH only in non-MFC C programs.

- [MFC exceptions](../mfc/exception-handling-in-mfc.md)

Use the [/EH](../build/reference/eh-exception-handling-model.md) compiler option to specify the type of exception handling to use in a project; C++ exception handling is the default. Do not mix the error handling mechanisms; for example, do not use C++ exceptions with structured exception handling. Using C++ exception handling makes your code more portable, and it allows you to handle exceptions of any type. For more information about the drawbacks of structured exception handling, see [Structured Exception Handling](structured-exception-handling-c-cpp.md). For advice about mixing MFC macros and C++ exceptions, see [Exceptions: Using MFC Macros and C++ Exceptions](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="in-this-section"></a>W tej sekcji

- [Modern C++ best practices for exceptions and error handling](errors-and-exception-handling-modern-cpp.md)

- [How to design for exception safety](how-to-design-for-exception-safety.md)

- [How to interface between exceptional and non-exceptional code](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [The try, catch, and throw Statements](try-throw-and-catch-statements-cpp.md)

- [Jak są obliczane bloki catch](how-catch-blocks-are-evaluated-cpp.md)

- [Exceptions and Stack Unwinding](exceptions-and-stack-unwinding-in-cpp.md)

- [Exception Specifications](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Nieobsługiwane wyjątki języka C++](unhandled-cpp-exceptions.md)

- [Połączenie wyjątków języka C (strukturalnych) i C++](mixing-c-structured-and-cpp-exceptions.md)

- [Structured Exception Handling (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](cpp-language-reference.md)</br>
[Obsługa wyjątku x64](../build/exception-handling-x64.md)</br>
[Exception Handling (C++/CLI and C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)

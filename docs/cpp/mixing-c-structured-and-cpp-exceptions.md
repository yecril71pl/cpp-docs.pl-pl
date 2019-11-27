---
title: Mieszanie języka C (Structured) C++ i wyjątków
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: e49731f1c81057002eaae2bef16cda4a5cf86f8d
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246457"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mieszanie języka C (Structured) C++ i wyjątków

Jeśli chcesz napisać przenośny kod, użycie obsługi wyjątków strukturalnych (SEH) w C++ programie nie jest zalecane. Czasami jednak może być konieczne skompilowanie przy użyciu [/EHa](../build/reference/eh-exception-handling-model.md) i zamieszanie wyjątków strukturalnych C++ oraz kodu źródłowego i wymaga pewnych funkcji do obsługi obu rodzajów wyjątków. Ponieważ program obsługi wyjątków strukturalnych nie ma koncepcji obiektów lub wyjątków z określonym typem, nie może obsłużyć C++ wyjątków zgłaszanych przez kod. C++ Programy obsługi **catch** mogą jednak obsługiwać wyjątki strukturalne. C++Składnia obsługi wyjątków (**try**, **throw**, **catch**) nie jest akceptowana przez kompilator języka C, ale składnia obsługi wyjątków strukturalnych ( **__try**, **__except**, **__finally**) jest obsługiwana C++ przez kompilator.

Aby [](../c-runtime-library/reference/set-se-translator.md) uzyskać informacje na temat obsługi wyjątków strukturalnych jako wyjątków, C++ zobacz _set_se_translator.

Jeśli Mieszasz strukturę i C++ wyjątki, weź pod uwagę następujące potencjalne problemy:

- Wyjątki C++ i wyjątki strukturalne nie mogą być mieszane w obrębie tej samej funkcji.

- Programy obsługi zakończenia (bloki **__finally** ) są zawsze wykonywane, nawet podczas rozwinięcia po wystąpieniu wyjątku.

- C++Obsługa wyjątków może przechwycić i zachować semantykę operacji unwind we wszystkich modułach skompilowanych za pomocą opcji kompilatora [/EH](../build/reference/eh-exception-handling-model.md) , które umożliwiają włączenie semantyki unwind.

- Istnieją sytuacje, w których funkcje destruktora nie są wywoływane dla wszystkich obiektów. Na przykład, jeśli wystąpi wyjątek strukturalny podczas próby wykonania wywołania funkcji przez niezainicjowany wskaźnik funkcji i ta funkcja przyjmuje jako parametry obiekty, które zostały skonstruowane przed wywołaniem, destruktory tych obiektów nie są wywoływane Podczas rozwinięcia stosu.

## <a name="next-steps"></a>Kolejne kroki

- [Korzystanie z setjmp lub longjmp C++ w programach](../cpp/using-setjmp-longjmp.md)

  Zobacz więcej informacji na temat używania `setjmp` i `longjmp` w C++ programach.

- [Obsługa wyjątków strukturalnych w języku C++](../cpp/exception-handling-differences.md)

  Zobacz przykłady sposobów C++ obsługi wyjątków strukturalnych.

## <a name="see-also"></a>Zobacz także

[Nowoczesne C++ najlepsze rozwiązania dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md)

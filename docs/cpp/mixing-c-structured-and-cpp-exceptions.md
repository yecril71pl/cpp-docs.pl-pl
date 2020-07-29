---
title: Mieszanie wyjątków C (Structured) i C++
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: 72ddde9bc284a005c77694d599a8e9a3908cb2d0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233694"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mieszanie wyjątków C (Structured) i C++

Jeśli chcesz napisać przenośny kod, użycie obsługi wyjątków strukturalnych (SEH) w programie C++ nie jest zalecane. Czasami jednak może być konieczne skompilowanie przy użyciu [/EHa](../build/reference/eh-exception-handling-model.md) i mieszanych wyjątków strukturalnych oraz kodu źródłowego C++ i wymaga pewnych funkcji do obsługi obu rodzajów wyjątków. Ponieważ program obsługi wyjątków strukturalnych nie ma koncepcji obiektów lub wyjątków z określonym typem, nie może obsłużyć wyjątków zgłoszonych przez kod języka C++. Jednak **`catch`** programy obsługi języka C++ mogą obsługiwać wyjątki strukturalne. Składnia obsługi wyjątków C++ ( **`try`** , **`throw`** , **`catch`** ) nie jest akceptowana przez kompilator C, ale składnia obsługi wyjątków strukturalnych (**__try**, **`__except`** , **`__finally`** ) jest obsługiwana przez kompilator języka C++.

Zobacz [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) , aby uzyskać informacje na temat obsługi wyjątków strukturalnych jako wyjątków C++.

Jeśli Mieszasz wyjątki ze strukturą i C++, weź pod uwagę następujące potencjalne problemy:

- Wyjątki C++ i wyjątki strukturalne nie mogą być mieszane w obrębie tej samej funkcji.

- Programy obsługi zakończenia ( **`__finally`** bloki) są zawsze wykonywane, nawet podczas rozwinięcia po wystąpieniu wyjątku.

- Obsługa wyjątków C++ umożliwia przechwytywanie i zachowanie semantyki operacji unwind we wszystkich modułach skompilowanych za pomocą opcji kompilatora [/EH](../build/reference/eh-exception-handling-model.md) , które umożliwiają włączenie semantyki unwind.

- Istnieją sytuacje, w których funkcje destruktora nie są wywoływane dla wszystkich obiektów. Na przykład, jeśli wystąpi wyjątek strukturalny podczas próby wykonania wywołania funkcji przez niezainicjowany wskaźnik funkcji i ta funkcja przyjmuje jako parametry obiekty, które zostały skonstruowane przed wywołaniem, destruktory tych obiektów nie są wywoływane podczas operacji unwindy stosu.

## <a name="next-steps"></a>Następne kroki

- [Korzystanie z setjmp lub longjmp w programach C++](../cpp/using-setjmp-longjmp.md)

  Zobacz więcej informacji na temat używania `setjmp` programów i `longjmp` w języku C++.

- [Obsługa wyjątków strukturalnych w języku C++](../cpp/exception-handling-differences.md)

  Zobacz przykłady sposobów obsługi wyjątków strukturalnych przy użyciu języka C++.

## <a name="see-also"></a>Zobacz także

[Nowoczesne najlepsze rozwiązania w języku C++ dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md)

---
title: Mieszanie wyjątków C (Structured) i C++
description: Jak mieszać obsługę wyjątków strukturalnych i wyjątki języka C++ oraz niektóre potencjalne problemy.
ms.date: 08/24/2020
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: 98ce2335ff3b08b7a5d71e03305c481ba068e5e6
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898410"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mieszanie wyjątków C (Structured) i C++

Jeśli chcesz napisać przenośny kod, użycie obsługi wyjątków strukturalnych (SEH) w programie C++ nie jest zalecane. Czasami jednak warto skompilować przy użyciu [`/EHa`](../build/reference/eh-exception-handling-model.md) i mieszać wyjątki strukturalne oraz kod źródłowy C++ i potrzebować pewnych funkcji do obsługi obu rodzajów wyjątków. Ponieważ program obsługi wyjątków strukturalnych nie ma koncepcji obiektów lub wyjątków z określonym typem, nie może obsłużyć wyjątków zgłoszonych przez kod języka C++. Jednak **`catch`** programy obsługi języka C++ mogą obsługiwać wyjątki strukturalne. Składnia obsługi wyjątków C++ ( **`try`** , **`throw`** , **`catch`** ) nie jest akceptowana przez kompilator C, ale składnia obsługi wyjątków strukturalnych ( **`__try`** , **`__except`** , **`__finally`** ) jest obsługiwana przez kompilator języka C++.

Zobacz [`_set_se_translator`](../c-runtime-library/reference/set-se-translator.md) , aby uzyskać informacje na temat obsługi wyjątków strukturalnych jako wyjątków C++.

Jeśli Mieszasz wyjątki ze strukturą i C++, weź pod uwagę następujące potencjalne problemy:

- Wyjątki C++ i wyjątki strukturalne nie mogą być mieszane w obrębie tej samej funkcji.

- Programy obsługi zakończenia ( **`__finally`** bloki) są zawsze wykonywane, nawet podczas rozwinięcia po wystąpieniu wyjątku.

- Obsługa wyjątków C++ może przechwycić i zachować semantykę operacji unwind we wszystkich modułach skompilowanych z [`/EH`](../build/reference/eh-exception-handling-model.md) opcjami kompilatora, które umożliwiają włączenie semantyki unwind.

- Mogą wystąpić sytuacje, w których funkcje destruktora nie są wywoływane dla wszystkich obiektów. Na przykład wyjątek strukturalny może wystąpić podczas próby wykonania wywołania funkcji za pomocą niezainicjowanego wskaźnika funkcji. Jeśli parametry funkcji są obiektami zbudowanymi przed wywołaniem, destruktory tych obiektów nie są wywoływane podczas operacji unwindy stosu.

## <a name="next-steps"></a>Następne kroki

- [Korzystanie `setjmp` z `longjmp` programów lub w języku C++](../cpp/using-setjmp-longjmp.md)

  Zobacz więcej informacji na temat używania `setjmp` programów i `longjmp` w języku C++.

- [Obsługa wyjątków strukturalnych w języku C++](../cpp/exception-handling-differences.md)

  Zobacz przykłady sposobów obsługi wyjątków strukturalnych przy użyciu języka C++.

## <a name="see-also"></a>Zobacz też

[Nowoczesne najlepsze rozwiązania w języku C++ dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md)

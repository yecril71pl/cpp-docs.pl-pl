---
title: Obsługa wyjątków języka C++
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling
ms.assetid: 65f80b44-9d0f-4d17-b910-07205a5c5c40
ms.openlocfilehash: bbdec38bf722ebb1e188af408bf3a413f6d6b8b7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222162"
---
# <a name="c-exception-handling"></a>Obsługa wyjątków języka C++

Język C++ zawiera wbudowaną obsługę zgłaszania i przechwytywania wyjątków. Podczas programowania w języku C++, prawie zawsze należy używać wbudowanej w C++ obsługi wyjątków opisanej w tej sekcji.

Aby włączyć obsługę wyjątków C++ w kodzie, należy użyć [/ehsc](../build/reference/eh-exception-handling-model.md).

## <a name="in-this-section"></a>W tej sekcji

To omówienie obsługi wyjątków C++ zawiera:

- [Try, catch i throw — instrukcje](../cpp/try-throw-and-catch-statements-cpp.md)

- [Jak są obliczane bloki catch](../cpp/how-catch-blocks-are-evaluated-cpp.md)

- [Wyjątki i Odwijanie stosu](../cpp/exceptions-and-stack-unwinding-in-cpp.md)

- [Specyfikacje wyjątków](../cpp/exception-specifications-throw-cpp.md)

- [noexcept](../cpp/noexcept-cpp.md)

- [Nieobsługiwane wyjątki języka C++](../cpp/unhandled-cpp-exceptions.md)

- [Połączenie wyjątków języka C (strukturalnych) i C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)

## <a name="support-for-earlier-mfc-exceptions"></a>Obsługa wcześniejszych wyjątków MFC

Począwszy od wersji 4.0 MFC zaczęli korzystać z funkcji mechanizm obsługi wyjątków C++. Chociaż zaleca się stosowanie obsługi wyjątków języka C++ w nowym kodzie, w MFC w wersji 4.0 i nowszych zachowano makra z poprzednich wersji MFC, aby nie wprowadzić problemów w starym kodzie. Makra i nowy mechanizm mogą być również łączone. Aby uzyskać informacje dotyczące mieszania makr i C++ wyjątków, obsługa oraz konwertowania starego kodu w celu użycia nowego mechanizmu, zobacz artykuły [wyjątków: Używanie makr MFC i C++ wyjątki](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) i [wyjątków: Konwertowanie z makr wyjątków MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md). Starsze makra wyjątków MFC, jeżeli użytkownik nadal z nich korzysta, szacowane są jako słowa kluczowe wyjątków języka C++. Zobacz [wyjątków: Zmiany w makrach wyjątków w wersji 3.0 lub nowszej](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)
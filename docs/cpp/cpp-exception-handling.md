---
title: Obsługa wyjątków języka C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling
- Visual C++, exception handling
ms.assetid: 65f80b44-9d0f-4d17-b910-07205a5c5c40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41abebbd73dc1cf72e35dcce88aa551be181061b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019645"
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

Począwszy od wersji 4.0 MFC zaczęli korzystać z funkcji mechanizm obsługi wyjątków C++. Chociaż zaleca się stosowanie obsługi wyjątków języka C++ w nowym kodzie, w MFC w wersji 4.0 i nowszych zachowano makra z poprzednich wersji MFC, aby nie wprowadzić problemów w starym kodzie. Makra i nowy mechanizm mogą być również łączone. Aby uzyskać informacje dotyczące mieszania makr i obsługi wyjątków C++ oraz konwertowania starego kodu w celu użycia nowego mechanizmu, zobacz artykuły [wyjątki: wykorzystanie makr MFC i wyjątków języka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) i [wyjątki: konwertowanie z MFC Makra wyjątków](../mfc/exceptions-converting-from-mfc-exception-macros.md). Starsze makra wyjątków MFC, jeżeli użytkownik nadal z nich korzysta, szacowane są jako słowa kluczowe wyjątków języka C++. Zobacz [wyjątki: zmiany w makrach wyjątków w wersji 3.0 lub nowszej](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)
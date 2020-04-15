---
title: Obsługa wyjątków w msvc
description: C++ language reference exception handling overview.
ms.date: 04/15/2020
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 0d60f49c6f1412925c19aaf497352940411b5d92
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396280"
---
# <a name="exception-handling-in-msvc"></a>Obsługa wyjątków w msvc

Wyjątek jest warunkiem błędu, możliwie poza kontrolą programu, który uniemożliwia kontynuowanie wykonywania programu wzdłuż zwykłej ścieżki. Niektóre operacje, w tym tworzenie obiektów, wejście/dane wyjściowe pliku i wywołania funkcji wykonane z innych modułów, są potencjalnymi źródłami wyjątków, nawet jeśli program działa poprawnie. Niezawodny kod przewiduje wyjątki i je obsługuje. Aby wykryć błędy logiczne, należy użyć potwierdzeń, a nie wyjątków (zobacz [Używanie potwierdzeń).](/visualstudio/debugger/c-cpp-assertions)

## <a name="kinds-of-exceptions"></a>Rodzaje wyjątków

Kompilator Microsoft C++ (MSVC) obsługuje trzy rodzaje obsługi wyjątków:

- [Obsługa wyjątków języka C++](errors-and-exception-handling-modern-cpp.md)

   W przypadku większości programów języka C++ należy użyć obsługi wyjątków języka C++. Jest bezpieczny dla typu i zapewnia, że destruktory obiektów są wywoływane podczas odwijania stosu.

- [Obsługa wyjątków strukturalnych](structured-exception-handling-c-cpp.md)

   System Windows dostarcza własny mechanizm wyjątków, o nazwie obsługa wyjątków strukturalnych (SEH). Nie jest zalecane dla programowania Języka C++ lub MFC. SEH należy używać tylko w programach innych niż MFC C.

- [Wyjątki MFC](../mfc/exception-handling-in-mfc.md)

   Od wersji 3.0, MFC używa wyjątków C++. Nadal obsługuje jego starszych wyjątków obsługi makr, które są podobne do wyjątków C++ w formularzu. Aby uzyskać porady dotyczące mieszania makr MFC i wyjątków C++, zobacz [Wyjątki: Używanie makr MFC i wyjątków C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

Użyj opcji kompilatora [/EH,](../build/reference/eh-exception-handling-model.md) aby określić model obsługi wyjątków do użycia w projekcie C++. Standardowa obsługa wyjątków języka C++ (**/EHsc**) jest wartością domyślną w nowych projektach języka C++ w programie Visual Studio.

Nie zaleca się mieszania mechanizmów obsługi wyjątków. Na przykład nie należy używać wyjątków Języka C++ z obsługą wyjątków strukturalnych. Za pomocą obsługi wyjątków C++ wyłącznie sprawia, że kod bardziej przenośne i umożliwia obsługę wyjątków dowolnego typu. Aby uzyskać więcej informacji na temat wad obsługi wyjątków strukturalnych, zobacz [Obsługa wyjątków strukturalnych](structured-exception-handling-c-cpp.md).

## <a name="in-this-section"></a>W tej sekcji

- [Nowoczesne najlepsze rozwiązania w języku C++ dotyczące wyjątków i obsługi błędów](errors-and-exception-handling-modern-cpp.md)

- [Jak projektować dla bezpieczeństwa wyjątków](how-to-design-for-exception-safety.md)

- [Instrukcje: interfejs między kodem obsługi wyjątków a innym kodem](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [Instrukcje try, catch i throw](try-throw-and-catch-statements-cpp.md)

- [Jak są obliczane bloki catch](how-catch-blocks-are-evaluated-cpp.md)

- [Wyjątki i odwijanie stosu](exceptions-and-stack-unwinding-in-cpp.md)

- [Specyfikacje wyjątków](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Nieobsługiwane wyjątki języka C++](unhandled-cpp-exceptions.md)

- [Połączenie wyjątków języka C (strukturalnych) i C++](mixing-c-structured-and-cpp-exceptions.md)

- [Obsługa wyjątków strukturalnych (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Zobacz też

[Odwołanie do języka języka C++](cpp-language-reference.md)</br>
[Obsługa wyjątku x64](../build/exception-handling-x64.md)</br>
[Obsługa wyjątków (C++/CLI i C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)

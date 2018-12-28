---
title: Obsługa wyjątków w języku Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: a155d56cc234c11534f5456ef92ea913e094f1a8
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627283"
---
# <a name="exception-handling-in-visual-c"></a>Obsługa wyjątków w języku Visual C++

Wyjątek jest warunkiem błędu, możliwie poza kontrolą programu, który uniemożliwia kontynuowanie wykonywania programu wzdłuż zwykłej ścieżki. Niektóre operacje, w tym tworzenie obiektu, odczyt z/zapis do pliku i wywołania funkcji z innych modułów, są potencjalnymi źródłami wyjątków, nawet wtedy, gdy program działa poprawnie. Niezawodny kod przewiduje wyjątki i je obsługuje.

Aby wykryć błędy logiczne w ramach pojedynczego programu lub modułu, należy używać asercji zamiast wyjątków (zobacz [wykorzystanie asercji](/visualstudio/debugger/c-cpp-assertions)).

Visual C++ wspiera trzy rodzaje obsługi wyjątków:

- [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)

   W większości programów, należy używać obsługę wyjątków C++, co jest bezpieczne względem typu i zapewnia wywołanie destruktorów obiektów podczas wykonywania operacji odwijania stosu.

- [Obsługa wyjątków strukturalnych](../cpp/structured-exception-handling-c-cpp.md)

   System Windows zawiera własny mechanizm wyjątków, nazywany SEH. Nie zaleca się stosowania tego systemu w programowaniu C++ lub MFC. SEH należy używać tylko w programach innych niż MFC c.

- [Wyjątki MFC](../mfc/exception-handling-in-mfc.md)

   Od wersji 3.0, MFC wykorzystuje wyjątki C++, ale nadal obsługuje jego starsze makra obsługi wyjątków, które mają podobną formę do wyjątków C++. Chociaż wykorzystanie tych makr nie jest zalecane w przypadku nowych programów, nadal są one obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami. W programach, które już używają makr, można bez ograniczeń wykorzystywać również wyjątki C++. Podczas wstępnego przetwarzania, makra szacują do słów kluczowych obsługi wyjątków zdefiniowanych w implementacji Visual C++ języka C++ od Visual C++ w wersji 2.0. Podczas korzystania z języka C++, można pozostawić na miejscu istniejące makra wyjątków.

Użyj [/EH](../build/reference/eh-exception-handling-model.md) opcję kompilatora, aby określić typ obsługi wyjątku do użycia w projekcie; Obsługa wyjątków języka C++ jest ustawieniem domyślnym. Nie należy mieszać mechanizmów; obsługi błędów na przykład nie należy używać wyjątków języka C++ z obsługi wyjątków strukturalnych. Przy użyciu obsługi wyjątków C++ sprawia, że Twój kod bardziej przenośny i pozwala obsługiwać wyjątki dowolnego typu. Aby uzyskać więcej informacji na temat wad strukturalna Obsługa wyjątków, zobacz [obsługi wyjątków strukturalnych](../cpp/structured-exception-handling-c-cpp.md). Aby uzyskać porady na temat mieszania makr MFC i wyjątków języka C++, zobacz [wyjątków: Używanie makr MFC i wyjątków C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

Aby uzyskać informacje dotyczące obsługi wyjątków w aplikacjach CLR, zobacz [obsługi wyjątków (C + +/ CLI i C + +/ CX)](../windows/exception-handling-cpp-component-extensions.md).

Aby uzyskać informacje dotyczące obsługi wyjątków na x64 procesorów, zobacz [x64 wyjątków](../build/exception-handling-x64.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)
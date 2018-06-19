---
title: Obsługa wyjątków w języku Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0acd5df644f097d19e5f9708f0a059a31f3e9ee9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413326"
---
# <a name="exception-handling-in-visual-c"></a>Obsługa wyjątków w języku Visual C++
Wyjątek jest warunkiem błędu, możliwie poza kontrolą programu, który uniemożliwia kontynuowanie wykonywania programu wzdłuż zwykłej ścieżki. Niektóre operacje, w tym tworzenie obiektu, odczyt z/zapis do pliku i wywołania funkcji z innych modułów, są potencjalnymi źródłami wyjątków, nawet wtedy, gdy program działa poprawnie. Niezawodny kod przewiduje wyjątki i je obsługuje.  
  
 Aby wykryć błędy logiczne w ramach jednego programu lub moduł, użyj potwierdzenia zamiast wyjątków (zobacz [przy użyciu potwierdzenia](/visualstudio/debugger/c-cpp-assertions)).  
  
 Visual C++ wspiera trzy rodzaje obsługi wyjątków:  
  
-   [C++, obsługa wyjątków](../cpp/cpp-exception-handling.md)  
  
     W większości programów, należy używać obsługę wyjątków C++, co jest bezpieczne względem typu i zapewnia wywołanie destruktorów obiektów podczas wykonywania operacji odwijania stosu.  
  
-   [Obsługa wyjątków strukturalnych](../cpp/structured-exception-handling-c-cpp.md)  
  
     System Windows zawiera własny mechanizm wyjątków, nazywany SEH. Nie zaleca się stosowania tego systemu w programowaniu C++ lub MFC. Użyj strukturalnej obsługi tylko w programach innych niż MFC C.  
  
-   [Wyjątków MFC](../mfc/exception-handling-in-mfc.md)  
  
     Od wersji 3.0, MFC wykorzystuje wyjątki C++, ale nadal obsługuje jego starsze makra obsługi wyjątków, które mają podobną formę do wyjątków C++. Chociaż wykorzystanie tych makr nie jest zalecane w przypadku nowych programów, nadal są one obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami. W programach, które już używają makr, można bez ograniczeń wykorzystywać również wyjątki C++. Podczas wstępnego przetwarzania, makra szacują do słów kluczowych obsługi wyjątków zdefiniowanych w implementacji Visual C++ języka C++ od Visual C++ w wersji 2.0. Podczas korzystania z języka C++, można pozostawić na miejscu istniejące makra wyjątków.  
  
 Użyj [/EH](../build/reference/eh-exception-handling-model.md) opcję kompilatora, aby określić typ obsługi wyjątków do użycia w projekcie; C++, obsługa wyjątków jest ustawieniem domyślnym. Nie należy ich łączyć obsługę mechanizmów; błędów na przykład nie należy używać wyjątków języka C++ z Obsługa wyjątków strukturalnych. Przy użyciu C++, obsługa wyjątków powoduje przenośną kodu i umożliwia obsługę wyjątków dowolnego typu. Aby uzyskać więcej informacji na temat wady Obsługa wyjątków strukturalnych, zobacz [obsługi wyjątków strukturalnych](../cpp/structured-exception-handling-c-cpp.md). Uzyskać porady na temat mieszanie makr MFC i wyjątków języka C++, zobacz [wyjątkami: za pomocą makr MFC i wyjątków języka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).  
  
 Aby uzyskać informacji na temat obsługi wyjątków w aplikacji do środowiska CLR, zobacz [obsługi wyjątków](../windows/exception-handling-cpp-component-extensions.md).  
  
 Aby uzyskać informacje o wyjątku obsługuje na x64 procesorów, zobacz [(x64) obsługi wyjątków](../build/exception-handling-x64.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)
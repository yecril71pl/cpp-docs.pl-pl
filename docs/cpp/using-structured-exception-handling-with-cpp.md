---
title: Przy użyciu obsługi wyjątków strukturalnych z C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, mixed with SEH
- structured exception handling [C++], with C++ exception handling
ms.assetid: ec34b528-8c26-4429-b24a-6a68553aaa91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 363dd00cd5f4e177ea32a109cf5f56a1f3c6cb29
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461728"
---
# <a name="using-structured-exception-handling-with-c"></a>Korzystanie z obsługi wyjątków strukturalnych za pomocą języka C++
Obsługa wyjątków strukturalnych, opisane w następujących artykułach działa z plikami źródłowymi C i C++. Jednak nie jest specjalnie zaprojektowana dla języka C++ i nie jest zalecane. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto mechanizm obsługi wyjątków C++ jest bardziej elastyczne, gdyż może obsługiwać wyjątki dowolnego typu.  
  
 Microsoft C++ obsługuje teraz model oparty na standardzie ANSI C++ obsługi wyjątków C++. Ten mechanizm obsługuje automatycznie niszczenie obiektów lokalnych podczas odwijania stosu. Jeśli piszesz odpornej na uszkodzenia kodu w języku C++ i chcesz zaimplementować obsługę wyjątków, zaleca się użycie C++ obsługi wyjątków, zamiast strukturalna Obsługa wyjątków. (Zwróć uwagę, że podczas obsługi konstrukcji, zgodnie z opisem w następujących artykułach wyjątków strukturalnych obsługiwanych przez kompilator C++, standardowa kompilator języka C nie obsługuje składnia obsługi wyjątków C++). Aby uzyskać szczegółowe informacje dotyczące obsługi wyjątków C++, zobacz [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md) i *Annotated C++ Reference Manual* autorstwa Margaret Ellis i Bjarne'a Stroustrupa.  
  
## <a name="see-also"></a>Zobacz także  
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
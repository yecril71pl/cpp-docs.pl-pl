---
title: "Przy użyciu obsługi z C++ wyjątków strukturalnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, mixed with SEH
- structured exception handling [C++], with C++ exception handling
ms.assetid: ec34b528-8c26-4429-b24a-6a68553aaa91
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db5d067a391512d56a2d01ce3052ac3fab061f28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-structured-exception-handling-with-c"></a>Korzystanie z obsługi wyjątków strukturalnych za pomocą języka C++
Obsługa wyjątków strukturalnych opisane w następujących artykułach działa zarówno C i C++ plików źródłowych. Jednak nie są specjalnie zaprojektowane dla języka C++ i nie jest zalecane. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto obsługa mechanizmu wyjątków C++ jest bardziej elastyczne i, w którym może obsłużyć wyjątki dowolnego typu.  
  
 Microsoft C++ obsługuje teraz model oparty na ANSI C++ Standard obsługi wyjątków C++. Ten mechanizm automatycznie obsługuje stosowanie i niszczenie obiektów lokalnych podczas unwind stosu. Jeśli piszesz kod w języku C++ odpornej na uszkodzenia i implementowania obsługi wyjątków, zdecydowanie zaleca się użycie C++ obsługi wyjątków, zamiast Obsługa wyjątków strukturalnych. (Pamiętaj, że kompilator języka C++ obsługuje obsługi konstrukcje, zgodnie z opisem w następujących artykułach wyjątków strukturalnych, standardowy kompilator C nie obsługują wyjątek języka C++, Obsługa składni). Aby uzyskać szczegółowe informacje dotyczące obsługi wyjątków języka C++, zobacz [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md) i *opatrzone adnotacjami podręcznika C++* Margaret Ellis i Bjarne Stroustrup.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
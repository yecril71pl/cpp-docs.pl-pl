---
title: "C++, obsługa wyjątków | Dokumentacja firmy Microsoft"
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
- C++ exception handling
- Visual C++, exception handling
ms.assetid: 65f80b44-9d0f-4d17-b910-07205a5c5c40
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6cbe3489b0d45111a527102c85e6d8c207715ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-exception-handling"></a>Obsługa wyjątków języka C++
Język C++ zawiera wbudowaną obsługę zgłaszania i przechwytywania wyjątków. Podczas programowania w języku C++, prawie zawsze należy używać wbudowanej w C++ obsługi wyjątków opisanej w tej sekcji.  
  
 Aby włączyć C++ obsługi wyjątków w kodzie, należy użyć [/ehsc](../build/reference/eh-exception-handling-model.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 To omówienie obsługi wyjątków C++ zawiera:  
  
-   [Try, catch i throw — instrukcje](../cpp/try-throw-and-catch-statements-cpp.md)  
  
-   [Jak są obliczane bloki przechwytywania](../cpp/how-catch-blocks-are-evaluated-cpp.md)  
  
-   [Wyjątki i Odwijanie stosu](../cpp/exceptions-and-stack-unwinding-in-cpp.md)  
  
-   [Specyfikacje wyjątków](../cpp/exception-specifications-throw-cpp.md)  
  
-   [noexcept](../cpp/noexcept-cpp.md)  
  
-   [Nieobsługiwane wyjątki języka C++](../cpp/unhandled-cpp-exceptions.md)  
  
-   [Połączenie wyjątków języka C (strukturalnych) i C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)  
  
## <a name="support-for-earlier-mfc-exceptions"></a>Obsługa wcześniejszych wyjątków MFC  
 Począwszy od wersji 4.0 MFC rozpoczęło się przy użyciu mechanizmu obsługi wyjątków C++. Chociaż zaleca się stosowanie obsługi wyjątków języka C++ w nowym kodzie, w MFC w wersji 4.0 i nowszych zachowano makra z poprzednich wersji MFC, aby nie wprowadzić problemów w starym kodzie. Makra i nowy mechanizm mogą być również łączone. Aby uzyskać informacje na temat mieszanie makr i C++, obsługa wyjątków oraz konwertowanie kodu starego do nowego mechanizmu, zobacz artykuły [wyjątkami: za pomocą makr MFC i wyjątków języka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) i [wyjątki: konwertowanie z MFC Makra wyjątków](../mfc/exceptions-converting-from-mfc-exception-macros.md). Starsze makra wyjątków MFC, jeżeli użytkownik nadal z nich korzysta, szacowane są jako słowa kluczowe wyjątków języka C++. Zobacz [wyjątki: zmiany w makrach wyjątków w wersji 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)
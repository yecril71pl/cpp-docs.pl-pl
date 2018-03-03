---
title: "Wyjątki: Używanie makr MFC i wyjątków języka C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6597f43deee73addff8e8f2045a38d7b1109fc0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Wyjątki: używanie makr MFC i wyjątków języka C++
W tym artykule omówiono zagadnienia dotyczące pisania kodu, który używa zarówno makra obsługi wyjątków MFC i słów kluczowych Obsługa wyjątków języka C++.  
  
 W tym artykule omówiono następujące tematy:  
  
-   [Mieszanie wyjątek słów kluczowych i makra](#_core_mixing_exception_keywords_and_macros)  
  
-   [Bloki try wewnątrz bloki catch](#_core_try_blocks_inside_catch_blocks)  
  
##  <a name="_core_mixing_exception_keywords_and_macros"></a>Mieszanie wyjątek słów kluczowych i makra  
 Można mieszać makr wyjątków MFC i słów kluczowych wyjątków C++ w ten sam program. Ale nie można mieszać makr MFC z słowa kluczowe języka C++ wyjątku, w tym samym bloku, ponieważ makra usunąć obiekty wyjątków automatycznie po ich się znaleźć poza zakresem, podczas gdy nie ma kodu za pomocą słowa kluczowe obsługi wyjątków. Aby uzyskać więcej informacji, zobacz artykuł [wyjątki: wyjątki połowowe i usuwania](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 Podstawowa różnica między makra i słów kluczowych jest, że makra "automatycznie" usunięcie zgłoszony wyjątek, jeśli wyjątek wykracza poza zakres. Kodowanie przy użyciu słów kluczowych nie; wyjątki przechwycone w bloku catch musi zostać jawnie usunięte. Mieszanie makr i słowa kluczowe języka C++ wyjątek może powodować przecieki pamięci, gdy nieusunięty obiekt wyjątku lub stercie uszkodzenie po usunięciu dwukrotnie wyjątek.  
  
 Następujący kod, na przykład unieważnia wskaźnika wyjątek:  
  
 [!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]  
  
 Problem występuje, ponieważ `e` jest usuwane podczas wykonywania przekazuje poza "wewnętrzna" **CATCH** bloku. Przy użyciu `THROW_LAST` makro zamiast **THROW** spowoduje, że instrukcja "zewnętrzne" **CATCH** bloku do odbierania prawidłowego wskaźnika:  
  
 [!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]  
  
##  <a name="_core_try_blocks_inside_catch_blocks"></a>Bloki wewnątrz bloków Catch try  
 Nie można ponownie zgłosić bieżącego wyjątku z poziomu **spróbuj** bloku, który znajduje się wewnątrz **CATCH** bloku. Poniższy przykład jest nieprawidłowy:  
  
 [!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]  
  
 Aby uzyskać więcej informacji, zobacz [wyjątki: badanie zawartości wyjątku](../mfc/exceptions-examining-exception-contents.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)


---
title: 'Wyjątki: Zmiany w makrach wyjątków w wersji 3.0 | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92d1691f9a61a11dc4d9dfe7e869ccb7899746bc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Wyjątki: zmiany w makrach wyjątków w wersji 3.0
Jest to zaawansowane tematu.  
  
 Makra obsługi wyjątków w wersji 3.0 i nowszych MFC, zostały zmienione używać wyjątków C++. W tym artykule wyjaśniono, jak te zmiany mogą wpływać na zachowanie istniejący kod, który korzysta z makra.  
  
 W tym artykule omówiono następujące tematy:  
  
-   [Typy wyjątków i makra CATCH](#_core_exception_types_and_the_catch_macro)  
  
-   [Ponownie zgłaszanie wyjątków](#_core_re.2d.throwing_exceptions)  
  
##  <a name="_core_exception_types_and_the_catch_macro"></a> Typy wyjątków i makra CATCH  
 We wcześniejszych wersjach MFC **CATCH** makro umożliwia określenie typu wyjątku informacje typu run-time MFC; określony typ wyjątku, innymi słowy, w obszarze przechwytywania. Wyjątków C++ jednak typ wyjątku jest zawsze określane w lokacji throw przez typ obiektu wyjątek zgłaszany. W rzadkich przypadkach, gdy typ wskaźnika do obiektu zgłoszenia różni się od typu obiektu zgłoszenia spowoduje niezgodności.  
  
 Poniższy przykład przedstawia konsekwencją tej różnicy między MFC w wersji 3.0 i wcześniejszych wersjach:  
  
 [!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]  
  
 Ten kod zachowuje się inaczej w wersji 3.0 lub nowszej, ponieważ formant zawsze przekazuje do pierwszej **catch** blok z pasujących deklaracji wyjątku. Wynik wyrażenia throw  
  
 [!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]  
  
 Zgłoszono jako **cexception —\***, nawet jeśli jest tworzony jako **CCustomException**. **CATCH** makr MFC wersji 2.5 i wcześniejszych zastosowań `CObject::IsKindOf` do testowania typu w czasie wykonywania. Ponieważ wyrażenie  
  
 [!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]  
  
 ma wartość true, pierwszy blok catch przechwytuje wyjątek. W wersji 3.0, która implementuje wiele makra Obsługa wyjątków za pomocą wyjątków języka C++, drugi blok catch zgodny element zgłaszany `CException`.  
  
 Kod podobny do tego jest rzadko. Zwykle wyświetlany, gdy obiekt wyjątku jest przekazywany do innej funkcji, który akceptuje ogólnego **cexception —\***, przetwarza "throw przed" i na koniec zgłasza wyjątek.  
  
 Aby obejść ten problem, Przenieś wyrażenia throw z funkcji do wywołującego kodu i Zgłoś wyjątek typu rzeczywistego nieznany wyjątek w czasie kompilator jest generowany.  
  
##  <a name="_core_re.2d.throwing_exceptions"></a> Ponownie zgłaszanie wyjątków  
 Blok catch nie można zgłosić tego samego wskaźnika wyjątek, który go przechwycony.  
  
 Na przykład tego kodu jest prawidłowa w poprzednich wersjach, ale będzie mieć nieoczekiwane wyniki w wersji 3.0:  
  
 [!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]  
  
 Przy użyciu **THROW** w catch bloku powoduje, że wskaźnik `e` do usunięcia, dzięki czemu witryny zewnętrzne catch otrzymają nieprawidłowego wskaźnika. Użyj `THROW_LAST` do ponowne generowanie `e`.  
  
 Aby uzyskać więcej informacji, zobacz [wyjątki: wyjątki połowowe i usuwania](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)


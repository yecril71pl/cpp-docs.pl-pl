---
title: "Wyjątki: Przechwytywanie i usuwanie wyjątków | Dokumentacja firmy Microsoft"
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
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8496b5228fe4002bb1ca80f8fbe793fd5e16ca81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Wyjątki: przechwytywanie i usuwanie wyjątków
Poniższe instrukcje i przykłady przedstawiają sposób catch i usuwanie wyjątków. Aby uzyskać więcej informacji na temat **spróbuj**, **catch**, i `throw` słów kluczowych, zobacz [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md).  
  
 Twoje programy obsługi wyjątków należy usunąć obiekty wyjątków, które obsługują, ponieważ nie powiodło się usunięcie wyjątek powoduje przeciek pamięci, zawsze, gdy wyjątek zostanie przechwycony przez ten kod.  
  
 Twoje **catch** bloku należy usunąć Wystąpił wyjątek podczas:  
  
-   **Catch** bloku zgłasza wyjątek nowe.  
  
     Nie musi, Usuń wyjątek, jeśli zgłosić ten sam wyjątek:  
  
     [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]  
  
-   Zwraca wykonywania z poziomu **catch** bloku.  
  
> [!NOTE]
>  Podczas usuwania `CException`, użyj **usunąć** funkcji członkowskiej można usunąć wyjątku. Nie używaj **usunąć** — słowo kluczowe, ponieważ jego może zakończyć się niepowodzeniem, jeśli wyjątek nie znajduje się na stercie.  
  
#### <a name="to-catch-and-delete-exceptions"></a>Aby przechwycić i usuwanie wyjątków  
  
1.  Użyj **spróbuj** — słowo kluczowe, aby skonfigurować **spróbuj** bloku. Wykonanie instrukcji dowolnego programu, które może zgłosić wyjątek w **spróbuj** bloku.  
  
     Użyj **catch** — słowo kluczowe, aby skonfigurować **catch** bloku. Umieść kod obsługi wyjątków w **catch** bloku. Kod w **catch** bloku jest wykonywane tylko wtedy, gdy kod w **spróbuj** bloku zgłasza wyjątek typu określonego w **catch** instrukcji.  
  
     Poniżej przedstawiono szkielet jak **spróbuj** i **catch** zwykle ułożone bloków:  
  
     [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]  
  
     Podczas wyjątek kontroli przechodzą do pierwszej **catch** bloku, w których deklaracji wyjątku jest zgodny z typem wyjątku. Można selektywnie obsługi różnych typów wyjątków z sekwencyjnych **catch** blokuje wymienione poniżej:  
  
     [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]  
  
 Aby uzyskać więcej informacji, zobacz [wyjątki: konwertowanie z makr wyjątków MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)


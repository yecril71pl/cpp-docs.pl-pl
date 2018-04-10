---
title: Obsługa błędów oraz powiadomienia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 738721eb3fc37ba076157129cb88a22f2c90e464
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="error-handling-and-notification"></a>Obsługa błędów oraz powiadomienia
Aby uzyskać więcej informacji o Obsługa błędów oraz powiadomienia, zobacz [opis funkcji Pomocnik](understanding-the-helper-function.md).  
  
 Aby uzyskać więcej informacji o funkcji punktów zaczepienia, zobacz [struktura i stała — definicje](../../build/reference/structure-and-constant-definitions.md).  
  
 Jeśli program korzysta z bibliotek DLL załadowanych z opóźnieniem, jego musi obsługiwać błędy niezawodnie od nieobsługiwanych wyjątków spowoduje błędów, które są wykonywane, gdy program jest uruchomiony. Obsługa awarii składa się z dwóch części:  
  
 Przywracanie do punktu zaczepienia.  
 Jeśli kod musi odzyskać lub podaj alternatywnej biblioteki i/lub procedury w przypadku niepowodzenia, można podać punktu zaczepienia funkcji pomocnika, które można podać lub rozwiązać tę sytuację. Kontynuować musi rutynowych haku zwrócić odpowiednią wartość, tak aby przetwarzania (wystąpienie HINSTANCE lub FARPROC) lub wpisz 0, aby wskazać, że zgłaszany wyjątek. Można go również throw własną wyjątek lub **longjmp** poza haka. Istnieją punkty zaczepienia powiadomień i punkty zaczepienia błędów.  
  
 Raportowanie za pośrednictwem wyjątku.  
 Jeśli wszystko, co jest niezbędne do obsługi błędu jest przerwanie procedura, nie haku niezbędnym tak długo, jak kod użytkownika może obsłużyć wyjątek.  
  
 W poniższych tematach opisano Obsługa błędów oraz powiadomienia:  
  
-   [Punkty zaczepienia powiadomień](../../build/reference/notification-hooks.md)  
  
-   [Punkty zaczepienia błędów](../../build/reference/failure-hooks.md)  
  
-   [Wyjątki](../../build/reference/exceptions-c-cpp.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)
---
title: Obsługa błędów oraz powiadomienia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2edec23da89766a45545566b0a689001d3ca75f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
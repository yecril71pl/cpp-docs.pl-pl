---
title: "Błąd PRJ0003 kompilacji projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0003
dev_langs:
- C++
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bcf80eb4d45fe1ae163772b96339c123996ae377
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="project-build-error-prj0003"></a>Błąd PRJ0003 kompilacji projektu  
  
> Błąd podczas duplikowania "*wiersza polecenia*".  
  
*Wiersza polecenia* polecenia utworzone z danych wejściowych w **strony właściwości** okno dialogowe zwrócił kod błędu, ale nie widać żadnych informacji w **dane wyjściowe** okna.  

Możliwe przyczyny tego błędu:  
  
-   Projekt zależy od serwera ATL. Począwszy od programu Visual Studio 2008, serwer ATL nie jest już częścią programu Visual Studio, ale zostało zwolnione jako projektu udostępnionego źródła w witrynie CodePlex. Aby pobrać kodu źródłowego serwera ATL i narzędzi, przejdź do [narzędzia i biblioteki serwera ATL.](http://go.microsoft.com/fwlink/p/?linkid=81979).  
  
-   Niewystarczające zasoby systemu. Zamknij niektóre aplikacje, aby rozwiązać ten problem.  
  
-   Niewystarczające uprawnienia zabezpieczeń. Sprawdź, czy masz wystarczające uprawnienia zabezpieczeń.  
  
-   Określone w ścieżki pliku wykonywalnego **katalogi VC ++** nie zawierają ścieżki narzędzia, który próbujesz uruchomić. Aby uzyskać informacje, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md)  
  
-   Dla projektów makefile brakuje polecenie do uruchomienia na albo **kompilacji wiersza polecenia** lub **odbudować wiersza polecenia**.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy i ostrzeżenia kompilowania projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
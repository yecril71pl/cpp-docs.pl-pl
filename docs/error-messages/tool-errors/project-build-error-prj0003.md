---
title: Błąd PRJ0003 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0003
dev_langs:
- C++
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a44f272569741b1897caed1d1d64832d8b113eae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0003"></a>Błąd PRJ0003 kompilacji projektu  
  
> Błąd podczas duplikowania "*wiersza polecenia*".  
  
*Wiersza polecenia* polecenia utworzone z danych wejściowych w **strony właściwości** okno dialogowe zwrócił kod błędu, ale nie widać żadnych informacji w **dane wyjściowe** okna.  

Możliwe przyczyny tego błędu:  
  
-   Projekt zależy od serwera ATL. Począwszy od programu Visual Studio 2008, serwer ATL nie jest już częścią programu Visual Studio, ale zostało zwolnione jako projektu udostępnionego źródła w witrynie CodePlex. Aby pobrać kodu źródłowego serwera ATL i narzędzi, przejdź do [narzędzia i biblioteki serwera ATL](http://go.microsoft.com/fwlink/p/?linkid=81979).  
  
-   Niewystarczające zasoby systemu. Zamknij niektóre aplikacje, aby rozwiązać ten problem.  
  
-   Niewystarczające uprawnienia zabezpieczeń. Sprawdź, czy masz wystarczające uprawnienia zabezpieczeń.  
  
-   Określone w ścieżki pliku wykonywalnego **katalogi VC ++** nie zawierają ścieżki narzędzia, który próbujesz uruchomić. Aby uzyskać informacje, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md)  
  
-   Dla projektów makefile brakuje polecenie do uruchomienia na albo **kompilacji wiersza polecenia** lub **odbudować wiersza polecenia**.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy i ostrzeżenia kompilowania projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
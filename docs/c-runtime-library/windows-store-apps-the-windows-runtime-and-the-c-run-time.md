---
title: "Aplikacje ze Sklepu Windows, środowiska uruchomieniowego systemu Windows i C Run-Time | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c75d66fcbe9ef437980878e7789a82dc94b68573
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="windows-store-apps-the-windows-runtime-and-the-c-run-time"></a>Aplikacje sklepu Windows Store, środowisko wykonawcze systemu Windows i środowisko wykonawcze języka C
[!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]aplikacje są programy, które działają w środowiska uruchomieniowego systemu Windows, która wykonuje na [!INCLUDE[win8](../build/reference/includes/win8_md.md)].  Środowisko wykonawcze systemu Windows jest wiarygodnego środowiska, która kontroluje, funkcje, zmienne i zasobów, które są dostępne dla [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikacji. Jednak zgodnie z projektem ograniczenia środowiska wykonawczego systemu Windows uniemożliwiać większość funkcji biblioteki wykonawcze języka C (CRT) w [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikacji.  
  
 Środowisko wykonawcze systemu Windows nie obsługuje następujące funkcje CRT:  
  
-   Większość funkcji CRT, które są powiązane z nieobsługiwanych funkcji.  
  
     Na przykład [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikacji nie można utworzyć procesu za pomocą `exec` i `spawn` rodzin procedury.  
  
     Gdy funkcja CRT nie jest obsługiwana w [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikacji, że fakt znajdują się w artykule o jego.  
  
-   Najbardziej wielobajtowe funkcji znaków i ciąg.  
  
     Jednak zarówno Unicode i ANSI tekst są obsługiwane.  
  
-   Aplikacje konsoli i argumenty wiersza polecenia.  
  
     Tradycyjne aplikacje komputerowe nadal obsługuje jednak konsoli i argumenty wiersza polecenia.  
  
-   Zmienne środowiskowe.  
  
-   Pojęcie bieżący katalog roboczy.  
  
-   [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]aplikacje i bibliotek DLL, które statycznie połączone z CRT, utworzony za pomocą [/MT](../build/reference/md-mt-ld-use-run-time-library.md) lub `/MTd` — opcje kompilatora.  
  
     Oznacza to, aplikacji, która korzysta z wielowątkowej, statycznej wersji CRT.  
  
-   Aplikację, która została skompilowana przy użyciu [/mdd](../build/reference/md-mt-ld-use-run-time-library.md) — opcja kompilatora.  
  
     Oznacza to, debugowania, wielowątkowej i specyficznej dla biblioteki DLL środowiska CRT. Takie aplikacja nie jest obsługiwana na [!INCLUDE[win8_appstore_long](../build/reference/includes/win8_appstore_long_md.md)].  
  
 Aby uzyskać pełną listę funkcji CRT, które nie są dostępne w [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikacji i sugestie dotyczące funkcji alternatywnych, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [Zgodność](../c-runtime-library/compatibility.md)   
 [Środowisko wykonawcze systemu Windows nieobsługiwane funkcje CRT](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)   
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)
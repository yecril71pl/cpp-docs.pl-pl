---
title: "Błąd PRJ0009 kompilacji projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0009
dev_langs: C++
helpviewer_keywords: PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0ee183c24cf330b54a335efbd0bbe2b00e18d209
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0009"></a>Błąd PRJ0009 kompilacji projektu
Kompilacji nie można otworzyć dziennika do zapisu.  
  
 **Upewnij się, że plik nie jest otwarty przez inny proces i nie jest zabezpieczony przed zapisem.**  
  
 Po ustawieniu **rejestrowanie kompilacji** właściwości **tak** i wykonywanie tworzenie lub odbudowywanie, Visual C++ nie można otworzyć dziennika kompilacji w trybie wyłączności.  
  
 Sprawdź **rejestrowanie kompilacji** ustawienie otwierając **opcje** okno dialogowe (na **narzędzia** menu, kliknij przycisk **opcje** polecenia), a następnie Wybieranie **kompilacji VC ++** w **projekty** folderu. Pliku kompilacji jest nazywany BuildLog.htm i jest zapisywany w katalogu pośrednim $(intdir —).  
  
 Możliwe przyczyny tego błędu:  
  
-   Uruchamiasz dwa procesy Visual C++ i w trakcie kompilacji tej samej konfiguracji tego samego projektu w obu jednocześnie.  
  
-   Plik dziennika kompilacji jest otwarty w procesie, która blokuje pliku.  
  
-   Użytkownik nie ma uprawnień do tworzenia pliku.  
  
-   Bieżący użytkownik nie ma dostępu do zapisu do pliku BuildLog.htm.
---
title: Błąd PRJ0009 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0009
dev_langs:
- C++
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5692ec643f5e3fe1adebf68048a6c435ab05d6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318457"
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
---
title: Błąd BSCMAKE BK1513 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93664a1224b85ec808805da0172aec408e875bc9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="bscmake-error-bk1513"></a>Błąd BSCMAKE BK1513
nieprzyrostowa aktualizacja wymaga wszystkich. SBR, pliki  
  
 BSCMAKE nie może utworzyć nowego pliku przeglądania informacji (.bsc), ponieważ jeden lub więcej plików SBR są obcinane. Aby znaleźć nazwy plików SBR obcięty, przeczytaj [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) ostrzeżenia dołączone do tego błędu.  
  
 BSCMAKE można zaktualizować pliku .bsc przy użyciu pliku .sbr obcięty, ale nie może utworzyć nowy. BSCMAKE może utworzyć nowego pliku .bsc z następujących powodów:  
  
-   Brak pliku .bsc.  
  
-   Niewłaściwy nie określono nazwy pliku dla pliku .bsc.  
  
-   Plik .bsc uszkodzony.  
  
 Aby rozwiązać ten problem, Usuń pliki SBR obcięty i skompiluj ponownie, lub wyczyść rozwiązanie i skompiluj ponownie. (W środowisku IDE, wybierz **kompilacji**, **czystą rozwiązania**, a następnie wybierz pozycję **kompilacji**, **Kompiluj ponownie rozwiązanie**.)
---
title: Błąd krytyczny C1092 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1092
dev_langs:
- C++
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8f5b5d903fe1fb2d3182a7b08f7bf82ddf334fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1092"></a>Błąd krytyczny C1092
Edytuj i Kontynuuj nie obsługuje zmiany typów danych. Tworzenie wymagane  
  
 Zmienione lub dodane do typu danych od czasu ostatniej zakończonej pomyślnie kompilacji.  
  
-   Edytuj i Kontynuuj nie obsługuje zmian do istniejących typów danych, w tym definicje klasy, struktury lub wyliczenia. Musisz zatrzymać debugowanie i kompilowania aplikacji.  
  
-   Edytuj i Kontynuuj nie obsługuje dodawania nowych typów danych, jeśli plik bazy danych programu, takie jak vc*x*pdb 0 (gdzie *x* jest wersję główną programu Visual C++ w użyciu) jest tylko do odczytu. Aby dodać typy danych, kompilator otworzyć plik PDB w trybie zapisu.  
  
### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>Aby usunąć ten błąd bez przerywania bieżącej sesji debugowania  
  
1.  Zmień typ danych do stanu sprzed rozpoczęcia błędu.  
  
2.  Z **debugowania** menu, wybierz **zastosowanie zmian kodu**.  
  
### <a name="to-remove-this-error-without-changing-your-source-code"></a>Aby usunąć ten błąd, bez konieczności zmieniania kodu źródłowego  
  
1.  Z **debugowania** menu, wybierz **Zatrzymaj debugowanie**.  
  
2.  Z **kompilacji** menu, wybierz **kompilacji**.  
  
 Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu](/visualstudio/debugger/supported-code-changes-cpp).
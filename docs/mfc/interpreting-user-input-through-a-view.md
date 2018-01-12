---
title: "Interpretowanie danych wejściowych użytkownika za pośrednictwem widoku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 263afe7b444722174d1787594f869087d606a235
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="interpreting-user-input-through-a-view"></a>Interpretowanie danych wprowadzonych przez użytkownika za pośrednictwem widoku
Inne funkcje Członkowskie widoku obsługi i interpretować wszystkie dane wejściowe użytkownika. Zazwyczaj określi funkcje Członkowskie obsługi wiadomości w klasie widoku do przetworzenia:  
  
-   Windows [wiadomości](../mfc/messages.md) wygenerowany przez akcje myszy i klawiatury.  
  
-   [Polecenia](../mfc/user-interface-objects-and-command-ids.md) z menu, przycisków paska narzędzi i klawiszy skrótów.  
  
 Te funkcje Członkowskie obsługi wiadomości zinterpretować następujące akcje jako danych wejściowych, wybór lub edytowania, przenoszenie danych do i z Schowka w tym:  
  
-   Ruchów myszy kliknięć, przeciąga i dwukrotne kliknięcia  
  
-   Uderzenia w klawisze  
  
-   Polecenia menu  
  
 Komunikaty systemu Windows, które dojść do widoku zależy od potrzeb aplikacji.  
  
 [Obsługa i mapowanie tematów komunikatów](../mfc/message-handling-and-mapping.md) wyjaśniono, jak przypisać elementów menu oraz inne obiekty interfejsu użytkownika poleceń i jak można powiązać z funkcjami programu obsługi poleceń. [Obsługa i mapowanie tematów komunikatów](../mfc/message-handling-and-mapping.md) również wyjaśniono, jak MFC kieruje poleceń i wysyła standardowe komunikaty systemu Windows do obiektów, które zawierają programy obsługi dla nich.  
  
 Na przykład aplikacja może wystąpić potrzeba wdrożenia bezpośredniego myszy Rysowanie w widoku. Bazgrołów pokazano sposób obsługi `WM_LBUTTONDOWN`, `WM_MOUSEMOVE`, i `WM_LBUTTONUP` wiadomości odpowiednio, aby rozpocząć, kontynuować i kończyć się rysowanie segment linii. Z drugiej strony czasami może być konieczne kliknięcie myszki w widoku jako zaznaczenia zinterpretować. W widoku `OnLButtonDown` funkcji obsługi by stwierdzić, czy rysowanie lub wybranie użytkownika. W przypadku wybrania opcji, program obsługi może określić, czy kliknięcie w granicach niektórych obiektów w widoku, a jeśli tak, zmiany były wyświetlane jako wybrany obiekt.  
  
 Widok może również obsługiwać niektórych poleceń menu, takich jak zasoby z menu Edycja na wycinanie, kopiowanie, wklej lub usuwanie wybranych danych korzystanie ze Schowka. Program obsługi spowodowałoby wywołanie niektóre członka dotyczące schowka funkcje klasy `CWnd` transferu elementu wybrane dane do lub ze Schowka.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie widoków](../mfc/using-views.md)


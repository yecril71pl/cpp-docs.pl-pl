---
title: Interpretowanie danych wejściowych użytkownika za pośrednictwem widoku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f62d64ed9479f1d1003536f8c4944b53d04d696f
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931993"
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
  
 Na przykład aplikacja może wystąpić potrzeba wdrożenia bezpośredniego myszy Rysowanie w widoku. Bazgrołów pokazano sposób obsługi wiadomości WM_LBUTTONDOWN, WM_MOUSEMOVE i WM_LBUTTONUP odpowiednio, aby rozpocząć, kontynuować i kończyć się rysowanie segment linii. Z drugiej strony czasami może być konieczne kliknięcie myszki w widoku jako zaznaczenia zinterpretować. W widoku `OnLButtonDown` funkcji obsługi by stwierdzić, czy rysowanie lub wybranie użytkownika. W przypadku wybrania opcji, program obsługi może określić, czy kliknięcie w granicach niektórych obiektów w widoku, a jeśli tak, zmiany były wyświetlane jako wybrany obiekt.  
  
 Widok może również obsługiwać niektórych poleceń menu, takich jak zasoby z menu Edycja na wycinanie, kopiowanie, wklej lub usuwanie wybranych danych korzystanie ze Schowka. Program obsługi spowodowałoby wywołanie niektóre członka dotyczące schowka funkcje klasy `CWnd` transferu elementu wybrane dane do lub ze Schowka.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie widoków](../mfc/using-views.md)


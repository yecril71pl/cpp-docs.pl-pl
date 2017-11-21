---
title: 'Kontenery: Stany elementu klienckiego | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f1048cdce98be99b13d306e9ff36eb75b30e43cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="containers-client-item-states"></a>Kontenery: stany elementu klienckiego
W tym artykule opisano różne stany, które element Klient przechodzi w okresie użytkowania.  
  
 Element kliencki przechodzi przez kilka stanów jako go jest tworzony, aktywowany, modyfikować i zapisywany. Po każdej aktualizacji zmian stanu elementu, wywołania framework [COleClientItem::OnChange](../mfc/reference/coleclientitem-class.md#onchange) z `OLE_CHANGED_STATE` powiadomień. Drugi parametr jest wartością z przedziału od **COleClientItem::ItemState** wyliczenia. Może być jedną z następujących czynności:  
  
-   **COleClientItem::emptyState**  
  
-   **COleClientItem::loadedState**  
  
-   **COleClientItem::openState**  
  
-   **COleClientItem::activeState**  
  
-   **COleClientItem::activeUIState**  
  
 W stanu pustego elementu klienta nie jest jeszcze całkowicie elementu. Pamięć została przydzielona dla niego, ale go nie została jeszcze zainicjowana z danymi elementu OLE. Jest to stan elementu klienta jest w został on utworzony za pośrednictwem wywołania **nowe** , ale nie zostało jeszcze poddane drugi etap tworzenia typowych dwuetapową.  
  
 W drugim kroku realizuje wywołanie `COleClientItem::CreateFromFile` lub innym **CreateFrom***xxxx* funkcji, całkowicie tworzenia elementu. Skojarzono danych OLE (z pliku lub z innego źródła, na przykład zawartość Schowka) `COleClientItem`-pochodzi z obiektu. Teraz elementu jest w stanie załadowany.  
  
 Gdy element ma został otwarty w oknie serwera zamiast otwarty w miejsce w dokumencie kontenera, jest w stanie open (lub całkowicie otwarte). W tym stanie kreskowania jest zwykle rysowane przez reprezentacja elementu w oknie kontenera, aby wskazać, czy element jest aktywny w innym miejscu.  
  
 Po aktywowaniu elementu w miejscu przekazaniem, zwykle tylko krótko mówiąc, do stanu aktywnego. Następnie wchodzi aktywny stan interfejsu użytkownika, w którym serwer został scalony jego menu, paski narzędzi i inne składniki interfejsu użytkownika z tymi kontenera. Obecność te składniki interfejsu użytkownika odróżnia aktywny stan interfejsu użytkownika w stanie aktywnym. W przeciwnym razie aktywny jest podobny do stanu aktywnego interfejsu użytkownika. Jeśli serwer obsługuje cofania, serwer jest wymagana do przechowywania informacji poprzedni stan elementu OLE, dopóki nie osiągnie stan załadowany lub otwarte.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery](../mfc/containers.md)   
 [Aktywacji](../mfc/activation-cpp.md)   
 [Kontenery: Powiadomienia elementów klienckich](../mfc/containers-client-item-notifications.md)   
 [Trackery](../mfc/trackers.md)   
 [Crecttracker — klasa](../mfc/reference/crecttracker-class.md)

---
title: "Przetwarzanie komunikatów powiadomień w miesiącu kalendarza kontrolki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d775d1f27be328a27e9b4bc843e1780a8efb02ad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Przetwarzanie komunikatów powiadomień w formantach kalendarza miesięcznego
Jak użytkownicy korzystają z formant kalendarza miesięcznego (wybranie daty i/lub wyświetlanie inny miesiąc), formantu (`CMonthCalCtrl`) wysyła komunikaty powiadomień do nadrzędnego okna, zazwyczaj obiekt widoku lub okna dialogowego. Obsługi tych wiadomości, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik wybierze nowy miesiąc, aby wyświetlić, musisz podać zestaw dat, które powinny być wyróżniony.  
  
 Okno właściwości można dodać obsługi powiadomień do klasy nadrzędnej dla tych wiadomości, które chcesz wdrożyć.  
  
 Poniższa lista zawiera opis różnych powiadomienia wysyłane przez formant kalendarza miesięcznego.  
  
-   **Mcn_getdaystate —** żąda informacji o tym, które dni powinna być wyświetlana pogrubione. Informacje dotyczące obsługi tego powiadomienia, sekcji [Ustawianie stanu dnia formantu kalendarza miesięcznego](../mfc/setting-the-day-state-of-a-month-calendar-control.md).  
  
-   **MCN_SELCHANGE** powiadamia element nadrzędny o zmianie wybranego datę lub zakres daty.  
  
-   **MCN_SELECT** powiadamia element nadrzędny, zgłaszający wyboru daty jawnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Formanty](../mfc/controls-mfc.md)


---
title: Przetwarzanie komunikatów powiadomień w miesiącu kalendarza kontrolki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce9906a738ed6c577f46d2919a5cdac80b877110
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930992"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Przetwarzanie komunikatów powiadomień w formantach kalendarza miesięcznego
Jak użytkownicy korzystają z formant kalendarza miesięcznego (wybranie daty i/lub wyświetlanie inny miesiąc), formantu (`CMonthCalCtrl`) wysyła komunikaty powiadomień do nadrzędnego okna, zazwyczaj obiekt widoku lub okna dialogowego. Obsługi tych wiadomości, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik wybierze nowy miesiąc, aby wyświetlić, musisz podać zestaw dat, które powinny być wyróżniony.  
  
 Okno właściwości można dodać obsługi powiadomień do klasy nadrzędnej dla tych wiadomości, które chcesz wdrożyć.  
  
 Poniższa lista zawiera opis różnych powiadomienia wysyłane przez formant kalendarza miesięcznego.  
  
-   Żądania mcn_getdaystate — informacje o tym, które dni powinna być wyświetlana pogrubione. Informacje dotyczące obsługi tego powiadomienia, sekcji [Ustawianie stanu dnia formantu kalendarza miesięcznego](../mfc/setting-the-day-state-of-a-month-calendar-control.md).  
  
-   Notifies MCN_SELCHANGE nadrzędnej, czy wybrane datę lub zakres daty została zmieniona.  
  
-   Notifies MCN_SELECT nadrzędnej, czy wprowadzono wyboru daty jawnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)


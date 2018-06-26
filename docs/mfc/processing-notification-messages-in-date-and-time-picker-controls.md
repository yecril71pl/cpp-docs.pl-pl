---
title: Przetwarzanie komunikatów powiadomień w selektora dat i godzin kontrolki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
dev_langs:
- C++
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 630792eb4bdd89cbe8081894c4ee026437568f3b
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930767"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Przetwarzanie komunikatów powiadomień w formantach selektora dat i godzin
Jak użytkownicy korzystają z datą i formant wyboru godziny, formantu (`CDateTimeCtrl`) wysyła komunikaty powiadomień do nadrzędnego okna, zazwyczaj obiekt widoku lub okna dialogowego. Obsługi tych wiadomości, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik otwiera selektora daty i godziny do wyświetlenia w formancie kalendarza miesięcznego osadzone, dtn_dropdown — powiadomienie jest wysyłane.  
  
 Okno właściwości można dodać obsługi powiadomień do klasy nadrzędnej dla tych wiadomości, które chcesz wdrożyć.  
  
 Poniższa lista zawiera opis różnych powiadomienia wysyłane przez formant wyboru daty i godziny.  
  
-   Dtn_dropdown — powiadamia użytkownika, który ma być wyświetlany nadrzędnej, czy miesiąc osadzonego formantu kalendarza. To powiadomienie jest wysyłane tylko wtedy, gdy styl DTS_UPDOWN nie została ustawiona. Aby uzyskać więcej informacji dotyczących tego powiadomienia, zobacz [podczas uzyskiwania dostępu do osadzonego formantu kalendarza miesięcznego](../mfc/accessing-the-embedded-month-calendar-control.md).  
  
-   Dtn_closeup — powiadamia nadrzędnej, czy miesiąc osadzonego formantu kalendarza zostanie zamknięte. To powiadomienie jest wysyłane tylko wtedy, gdy styl DTS_UPDOWN nie została ustawiona.  
  
-   Dtn_datetimechange — Notifies nadrzędnej, czy nastąpiła zmiana w formancie.  
  
-   Dtn_format — powiadamia nadrzędnej, czy tekst jest potrzebne do wyświetlenia w polu. Aby uzyskać więcej informacji dotyczących tego pola wywołania zwrotnego i powiadomień, zobacz [za pomocą pola wywołania zwrotnego w dniu i o formant wyboru godziny](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
-   Dtn_formatquery — żądania nadrzędnego do dostarczania maksymalny dozwolony rozmiar ciągu, który będzie wyświetlany w polu. Obsługa tego powiadomienia umożliwia sterowanie prawidłowo wyświetlania wyniku cały czas Zmniejszanie migotania w wyświetlania formantu. Aby uzyskać więcej informacji dotyczących tego powiadomienia, zobacz [za pomocą pola wywołania zwrotnego w dniu i o formant wyboru godziny](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
-   Powiadamia DTN_USERSTRING kontrolować nadrzędnej, że użytkownik zakończył edycję zawartości selektora daty i godziny. To powiadomienie jest wysyłane tylko wtedy, gdy styl DTS_APPCANPARSE została ustawiona.  
  
-   DTN_WMKEYDOWN powiadamia element nadrzędny, gdy użytkownik wpisze w polu. Obsługa tego powiadomienia, aby emulować sama odpowiedź klawiatury obsługiwany w przypadku pól z systemem innym niż wywołania zwrotnego w formancie selektora daty i godziny. Aby uzyskać więcej informacji dotyczących tego powiadomienia, zobacz [obsługi pola wywołania zwrotnego w kontrolce DTP](http://msdn.microsoft.com/library/windows/desktop/bb761726) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)


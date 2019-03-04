---
title: Przetwarzanie komunikatów powiadomień w formantach selektora dat i godzin
ms.date: 11/04/2016
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
ms.openlocfilehash: ce84863744629d30248f94b94448d776177f9841
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292890"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Przetwarzanie komunikatów powiadomień w formantach selektora dat i godzin

Jak użytkownicy wchodzić w interakcje z datą i formant selektora czasu, kontrolka (`CDateTimeCtrl`) wysyła powiadomienia do okna nadrzędnego, zazwyczaj obiekt widoku lub w oknie dialogowym. Obsługiwać te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik otworzy selektora daty i godziny, aby wyświetlić formant kalendarza miesięcznego osadzony, dtn_dropdown — powiadomienie jest wysyłane.

Okno właściwości do dodania obsługi powiadomień do klasy nadrzędnej dla tych wiadomości, które chcesz wdrożyć.

Poniższa lista zawiera opis różnych powiadomień wysyłany przez kontrolkę selektora daty i godziny.

- Dtn_dropdown — powiadamia użytkownika, który ma być wyświetlany obiektu nadrzędnego, który miesiąca osadzonego formantu kalendarza. To powiadomienie jest wysyłane tylko wtedy, gdy styl DTS_UPDOWN nie została ustawiona. Aby uzyskać więcej informacji na temat tego powiadomienia, zobacz [uzyskiwania dostępu do osadzonego formantu kalendarza miesięcznego](../mfc/accessing-the-embedded-month-calendar-control.md).

- Dtn_closeup — powiadamia obiektu nadrzędnego, który miesiąca osadzonego formantu kalendarza zostanie zamknięte. To powiadomienie jest wysyłane tylko wtedy, gdy styl DTS_UPDOWN nie została ustawiona.

- Dtn_datetimechange — Notifies obiektu nadrzędnego, który nastąpiła zmiana w formancie.

- Powiadamia DTN_FORMAT obiektu nadrzędnego, który tekst jest wymagane do wyświetlenia w polu. Aby uzyskać więcej informacji na temat tego powiadomienia i pól wywołania zwrotnego, zobacz [przy użyciu pól wywołania zwrotnego, daty i czasu kontrolkę selektora](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

- Dtn_formatquery — żądań, nadrzędnego do dostarczania maksymalny dozwolony rozmiar ciągu, która będzie wyświetlana w polu. Obsługa to powiadomienie pozwala formant aby prawidłowo dane wyjściowe cały czas celi zmniejszenia migotania w ramach wyświetlania kontrolki. Aby uzyskać więcej informacji na temat tego powiadomienia, zobacz [przy użyciu pól wywołania zwrotnego, daty i czasu kontrolkę selektora](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_USERSTRING powiadamia element nadrzędny, że użytkownik zakończył edycję zawartości selektora daty i godziny jest kontrolować. To powiadomienie jest wysyłane tylko wtedy, gdy styl DTS_APPCANPARSE została ustawiona.

- DTN_WMKEYDOWN powiadamia element nadrzędny, gdy użytkownik wpisuje w polu. Obsługuj to powiadomienie, aby emulować tę samą odpowiedź klawiatury obsługiwany w przypadku pól bez wywołania zwrotnego w kontrolce selektora daty i godziny. Aby uzyskać więcej informacji na temat tego powiadomienia, zobacz [obsługi pól wywołania zwrotnego w kontrolce DTP](/windows/desktop/Controls/date-and-time-picker-controls) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

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
ms.openlocfilehash: 3c568d231cc02b2529a4d97ab7faed51c1737b19
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621007"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Przetwarzanie komunikatów powiadomień w formantach selektora dat i godzin

Gdy użytkownicy współpracują z kontrolką selektora daty i godziny, formant ( `CDateTimeCtrl` ) wysyła komunikaty powiadomień do okna nadrzędnego, zwykle widok lub obiekt okna dialogowego. Obsługuj te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład po otwarciu przez użytkownika selektora daty i godziny w celu wyświetlenia formantu kalendarza z osadzonym miesiącem zostanie wysłane powiadomienie DTN_DROPDOWN.

Użyj [kreatora klas](reference/mfc-class-wizard.md) , aby dodać programy obsługi powiadomień do klasy nadrzędnej dla tych komunikatów, które mają zostać wdrożone.

Na poniższej liście opisano różne powiadomienia wysyłane przez kontrolkę selektora daty i godziny.

- DTN_DROPDOWN powiadamia element nadrzędny, który ma zostać wyświetlony formant kalendarza osadzonego miesiąca. To powiadomienie jest wysyłane tylko wtedy, gdy styl DTS_UPDOWN nie został ustawiony. Aby uzyskać więcej informacji na temat tego powiadomienia, zobacz [dostęp do kontrolki kalendarza osadzonego miesiąca](accessing-the-embedded-month-calendar-control.md).

- DTN_CLOSEUP powiadamia element nadrzędny o tym, że formant kalendarza z osadzonym miesiącem ma zostać zamknięty. To powiadomienie jest wysyłane tylko wtedy, gdy styl DTS_UPDOWN nie został ustawiony.

- DTN_DATETIMECHANGE powiadamia element nadrzędny o wystąpieniu zmiany w kontrolce.

- DTN_FORMAT powiadamia element nadrzędny o tym, że tekst musi być wyświetlany w polu wywołania zwrotnego. Aby uzyskać więcej informacji na temat tego powiadomienia i pól wywołania zwrotnego, zobacz [Używanie pól wywołania zwrotnego w kontrolce selektora dat i godzin](using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_FORMATQUERY żąda elementu nadrzędnego w celu dostarczenia maksymalnego dozwolonego rozmiaru ciągu, który będzie wyświetlany w polu wywołania zwrotnego. Obsługa tego powiadomienia pozwala formantowi prawidłowo wyświetlać dane wyjściowe przez cały czas, skracając migotanie w obrębie ekranu kontrolki. Aby uzyskać więcej informacji na temat tego powiadomienia, zobacz [Używanie pól wywołania zwrotnego w kontrolce selektora dat i godzin](using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_USERSTRING powiadamia element nadrzędny, że użytkownik zakończył Edytowanie zawartości kontrolki selektora daty i godziny. To powiadomienie jest wysyłane tylko wtedy, gdy ustawiono styl DTS_APPCANPARSE.

- DTN_WMKEYDOWN powiadamia element nadrzędny, gdy użytkownik wpisze wartość pola wywołania zwrotnego. Obsłuż to powiadomienie, aby emulować tę samą odpowiedź klawiatury, która jest obsługiwana dla pól bez wywołania zwrotnego w kontrolce selektora dat i godzin. Aby uzyskać więcej informacji na temat tego powiadomienia, zobacz temat [Obsługa pól wywołania zwrotnego w kontrolce DTP](/windows/win32/Controls/date-and-time-picker-controls) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[Formanty](controls-mfc.md)

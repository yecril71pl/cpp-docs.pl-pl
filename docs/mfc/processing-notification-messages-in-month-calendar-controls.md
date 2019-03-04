---
title: Przetwarzanie komunikatów powiadomień w formantach kalendarza miesięcznego
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
ms.openlocfilehash: fc0bb475a95450c281c92b500083c9502df50931
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280761"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Przetwarzanie komunikatów powiadomień w formantach kalendarza miesięcznego

Jak użytkownicy oddziałują formant kalendarza miesięcznego (wybranie daty i/lub wyświetlanie innego miesiąca), kontrolki (`CMonthCalCtrl`) wysyła powiadomienia do okna nadrzędnego, zazwyczaj obiekt widoku lub w oknie dialogowym. Obsługiwać te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik wybierze na nowy miesiąc, aby wyświetlić, możesz podać zestaw dat, które powinny zostać.

Okno właściwości do dodania obsługi powiadomień do klasy nadrzędnej dla tych wiadomości, które chcesz wdrożyć.

Poniższa lista zawiera opis różnych powiadomień wysyłanych przez formant kalendarza miesięcznego.

- Informacje o mcn_getdaystate — żądania o tym, które dni powinien być wyświetlany czcionką pogrubioną. Aby uzyskać informacje dotyczące obsługi tego powiadomienia, zobacz [Ustawianie stanu dnia formantu kalendarza miesięcznego](../mfc/setting-the-day-state-of-a-month-calendar-control.md).

- Notifies MCN_SELCHANGE obiektu nadrzędnego, który wybranej daty lub zakres data została zmieniona.

- Notifies MCN_SELECT obiektu nadrzędnego, który wprowadził wybór daty jawne.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

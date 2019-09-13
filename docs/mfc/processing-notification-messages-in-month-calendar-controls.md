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
ms.openlocfilehash: 452d24bf1ffd157366f357a510e8c8cfaad28d91
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908082"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Przetwarzanie komunikatów powiadomień w formantach kalendarza miesięcznego

Gdy użytkownicy współpracują z kontrolką kalendarza miesięcznego (wybierając daty i/lub wyświetlając inny miesiąc), formant`CMonthCalCtrl`() wysyła komunikaty powiadomień do okna nadrzędnego, zazwyczaj jest to widok lub obiekt okna dialogowego. Obsługuj te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład, gdy użytkownik wybierze nowy miesiąc do wyświetlenia, można podać zestaw dat, które należy wyróżnić.

Użyj [kreatora klas](reference/mfc-class-wizard.md) , aby dodać programy obsługi powiadomień do klasy nadrzędnej dla tych komunikatów, które mają zostać wdrożone.

Na poniższej liście opisano różne powiadomienia wysyłane przez formant kalendarza miesięcznego.

- MCN_GETDAYSTATE żąda informacji o liczbie dni, które powinny być wyświetlane pogrubioną czcionką. Aby uzyskać informacje na temat obsługi tego powiadomienia, zobacz [Ustawianie stanu dnia formantu kalendarza miesięcznego](../mfc/setting-the-day-state-of-a-month-calendar-control.md).

- MCN_SELCHANGE powiadamia element nadrzędny o zmianie wybranej daty lub zakresu daty.

- MCN_SELECT powiadamia element nadrzędny o tym, że został wprowadzony jawny wybór daty.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

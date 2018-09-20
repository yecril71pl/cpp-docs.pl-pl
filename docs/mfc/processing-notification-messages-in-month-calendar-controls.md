---
title: Przetwarzanie komunikatów powiadomień w ciągu miesiąca w kalendarzu kontrolki | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5bbdb3728009cdee978bb08ef8df8817f1ef5e41
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378179"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Przetwarzanie komunikatów powiadomień w formantach kalendarza miesięcznego

Jak użytkownicy oddziałują formant kalendarza miesięcznego (wybranie daty i/lub wyświetlanie innego miesiąca), kontrolki (`CMonthCalCtrl`) wysyła powiadomienia do okna nadrzędnego, zazwyczaj obiekt widoku lub w oknie dialogowym. Obsługiwać te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik wybierze na nowy miesiąc, aby wyświetlić, możesz podać zestaw dat, które powinny zostać.

Okno właściwości do dodania obsługi powiadomień do klasy nadrzędnej dla tych wiadomości, które chcesz wdrożyć.

Poniższa lista zawiera opis różnych powiadomień wysyłanych przez formant kalendarza miesięcznego.

- Informacje o mcn_getdaystate — żądania o tym, które dni powinien być wyświetlany czcionką pogrubioną. Aby uzyskać informacje dotyczące obsługi tego powiadomienia, zobacz [Ustawianie stanu dnia formantu kalendarza miesięcznego](../mfc/setting-the-day-state-of-a-month-calendar-control.md).

- Notifies MCN_SELCHANGE obiektu nadrzędnego, który wybranej daty lub zakres data została zmieniona.

- Notifies MCN_SELECT obiektu nadrzędnego, który wprowadził wybór daty jawne.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)


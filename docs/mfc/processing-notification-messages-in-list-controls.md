---
title: Przetwarzanie komunikatów powiadomień w kontrolkach listy
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: 92111e3e0a4869ca06b89d2d18d38aab9f10ab7d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908092"
---
# <a name="processing-notification-messages-in-list-controls"></a>Przetwarzanie komunikatów powiadomień w kontrolkach listy

Gdy użytkownicy klikają nagłówki kolumn, przeciągają ikony, edytują etykiety i tak dalej, formant listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) wysyła komunikaty powiadomień do okna nadrzędnego. Obsługuj te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład, gdy użytkownik kliknie nagłówek kolumny, możesz chcieć posortować elementy na podstawie zawartości klikniętej kolumny, tak jak w programie Microsoft Outlook.

Przetwarzaj komunikaty WM_NOTIFY z formantu listy w swojej klasie widoków lub oknie dialogowym. Użyj [kreatora klas](reference/mfc-class-wizard.md) , aby utworzyć funkcję procedury obsługi [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) za pomocą instrukcji switch na podstawie tego, który komunikat powiadomienia jest obsługiwany.

Aby uzyskać listę powiadomień wysyłanych przez formant listy do okna nadrzędnego, zobacz temat informacje o [kontrolce widoku listy](/windows/win32/Controls/list-view-control-reference) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

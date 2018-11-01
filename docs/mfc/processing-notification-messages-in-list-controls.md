---
title: Przetwarzanie komunikatów powiadomień w kontrolkach listy
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: 427abe5259334588b566656abd70acf22b923809
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490093"
---
# <a name="processing-notification-messages-in-list-controls"></a>Przetwarzanie komunikatów powiadomień w kontrolkach listy

Użytkownik kliknie przycisk nagłówków kolumn, przeciągnij ikony, Edytuj etykiety i tak dalej, kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) wysyła powiadomienia do okna nadrzędnego. Obsługiwać te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik kliknie nagłówek kolumny, możesz chcieć posortować elementy na podstawie zawartości kliknięto kolumnę, tak jak w programie Microsoft Outlook.

Przetwarzanie wiadomości WM_NOTIFY z formantu listy w klasie widoku lub w oknie dialogowym. Okno właściwości, aby utworzyć [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi za pomocą instrukcji switch oparte na komunikat powiadomienia, które jest obsługiwane.

Aby uzyskać listę powiadomień wysłać kontrolkę listy do okna nadrzędnego, zobacz [odwołania kontrolka widoku listy](/windows/desktop/Controls/list-view-control-reference) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)


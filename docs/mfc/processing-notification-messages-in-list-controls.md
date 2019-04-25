---
title: Przetwarzanie komunikatów powiadomień w kontrolkach listy
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: 2a7899c74bfcddcdc8d54f7d9eb894553115ad66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160188"
---
# <a name="processing-notification-messages-in-list-controls"></a>Przetwarzanie komunikatów powiadomień w kontrolkach listy

Użytkownik kliknie przycisk nagłówków kolumn, przeciągnij ikony, Edytuj etykiety i tak dalej, kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) wysyła powiadomienia do okna nadrzędnego. Obsługiwać te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik kliknie nagłówek kolumny, możesz chcieć posortować elementy na podstawie zawartości kliknięto kolumnę, tak jak w programie Microsoft Outlook.

Przetwarzanie wiadomości WM_NOTIFY z formantu listy w klasie widoku lub w oknie dialogowym. Okno właściwości, aby utworzyć [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi za pomocą instrukcji switch oparte na komunikat powiadomienia, które jest obsługiwane.

Aby uzyskać listę powiadomień wysłać kontrolkę listy do okna nadrzędnego, zobacz [odwołania kontrolka widoku listy](/windows/desktop/Controls/list-view-control-reference) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

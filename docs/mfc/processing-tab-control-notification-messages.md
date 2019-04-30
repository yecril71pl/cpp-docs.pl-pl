---
title: Przetwarzanie komunikatów powiadomień dotyczących formantu karty
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
ms.openlocfilehash: 4be9074f3e7d7ce4321402d27fc26283a52436e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391390"
---
# <a name="processing-tab-control-notification-messages"></a>Przetwarzanie komunikatów powiadomień dotyczących formantu karty

Użytkownik kliknie przycisk, karty lub przyciski, formantu karty ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) wysyła powiadomienia do okna nadrzędnego. Obsługiwać te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik kliknie kartę, można wstępnie ustawione dane formantu na stronie przed wyświetleniem go.

Przetwarzanie wiadomości WM_NOTIFY z kontrolki karty w klasie widoku lub w oknie dialogowym. Okno właściwości, aby utworzyć [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi za pomocą instrukcji switch oparte na komunikat powiadomienia, które jest obsługiwane. Aby uzyskać listę powiadomień formant karty można wysyłać do okna nadrzędnego, zobacz **powiadomienia** części [odniesienie do formantu karty](/windows/desktop/controls/tab-control-reference) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

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
ms.openlocfilehash: 32e1b5954bc3f09f16c5516fc1c143dac716bc41
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693235"
---
# <a name="processing-tab-control-notification-messages"></a>Przetwarzanie komunikatów powiadomień dotyczących formantu karty

Użytkownik kliknie przycisk, karty lub przyciski, formantu karty ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) wysyła powiadomienia do okna nadrzędnego. Obsługiwać te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik kliknie kartę, można wstępnie ustawione dane formantu na stronie przed wyświetleniem go.

Przetwarzanie wiadomości WM_NOTIFY z kontrolki karty w klasie widoku lub w oknie dialogowym. Okno właściwości, aby utworzyć [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi za pomocą instrukcji switch oparte na komunikat powiadomienia, które jest obsługiwane. Aby uzyskać listę powiadomień formant karty można wysyłać do okna nadrzędnego, zobacz **powiadomienia** części [odniesienie do formantu karty](/windows/desktop/controls/tab-control-reference) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)


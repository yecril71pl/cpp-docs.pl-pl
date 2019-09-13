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
ms.openlocfilehash: cc322a038717d48f440df1ec571674cec80743ce
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908063"
---
# <a name="processing-tab-control-notification-messages"></a>Przetwarzanie komunikatów powiadomień dotyczących formantu karty

Gdy użytkownik kliknie karty lub przyciski, formant karty ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) wysyła komunikaty powiadomień do okna nadrzędnego. Obsługuj te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład, gdy użytkownik kliknie kartę, możesz chcieć wstępnie ustawić dane kontroli na stronie przed jej wyświetleniem.

Przetwarzaj komunikaty WM_NOTIFY z kontrolki karta w widoku lub w klasie okna dialogowego. Użyj [kreatora klas](reference/mfc-class-wizard.md) , aby utworzyć funkcję procedury obsługi [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) za pomocą instrukcji switch na podstawie tego, który komunikat powiadomienia jest obsługiwany. Aby uzyskać listę powiadomień, które formant karty może wysłać do okna nadrzędnego, zobacz sekcję **powiadomienia** w temacie Informacje o [kontrolkach kart](/windows/win32/controls/tab-control-reference) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

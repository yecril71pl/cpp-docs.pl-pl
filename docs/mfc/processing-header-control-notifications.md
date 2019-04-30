---
title: Przetwarzanie powiadomień dotyczących formantu karty
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
ms.openlocfilehash: 3c5d147741123f97a53b18a854db9204738d0a2f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339620"
---
# <a name="processing-header-control-notifications"></a>Przetwarzanie powiadomień dotyczących formantu karty

W klasie widoku lub w oknie dialogowym, użyj okna właściwości, aby utworzyć [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi za pomocą instrukcji switch dla każdego formantu nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) komunikaty powiadomień, które mają być Obsługa (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)). Powiadomienia są wysyłane do okna nadrzędnego, gdy użytkownik kliknie przycisk lub kliknie dwukrotnie element nagłówka drags na linię podziału między elementami i tak dalej.

Powiadomienia związane z formantem nagłówka są wymienione w [odwołanie do formantu nagłówka](/windows/desktop/controls/header-control-reference) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

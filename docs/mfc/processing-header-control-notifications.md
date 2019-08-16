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
ms.openlocfilehash: f60a0c918476702881984f976b220130727cf4b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507942"
---
# <a name="processing-header-control-notifications"></a>Przetwarzanie powiadomień dotyczących formantu karty

W widoku lub klasie okna dialogowego Użyj okno Właściwości, aby utworzyć funkcję procedury obsługi [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) z instrukcją Switch dla wszelkich komunikatów powiadomień nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)), które chcesz obsłużyć (zobacz [Mapowanie komunikatów do funkcji ](../mfc/reference/mapping-messages-to-functions.md)). Powiadomienia są wysyłane do okna nadrzędnego, gdy użytkownik kliknie lub dwukrotnie kliknie element nagłówka, przeciągnie dzielnika między elementami itd.

Komunikaty powiadomień skojarzone z kontrolką nagłówka są wymienione w temacie [Informacje o formancie nagłówka](/windows/win32/controls/header-control-reference) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

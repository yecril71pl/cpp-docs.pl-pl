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
ms.openlocfilehash: c313382b8be7538ba5bb465c6ba383955e414662
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619796"
---
# <a name="processing-header-control-notifications"></a>Przetwarzanie powiadomień dotyczących formantu karty

W widoku lub klasie okna dialogowego Użyj [kreatora klas](reference/mfc-class-wizard.md) , aby utworzyć funkcję procedury obsługi [OnChildNotify](reference/cwnd-class.md#onchildnotify) z instrukcją Switch dla wszelkich komunikatów powiadomień nagłówka ([CHeaderCtrl](reference/cheaderctrl-class.md)), które chcesz obsłużyć (zobacz [Mapowanie komunikatów do funkcji](reference/mapping-messages-to-functions.md)). Powiadomienia są wysyłane do okna nadrzędnego, gdy użytkownik kliknie lub dwukrotnie kliknie element nagłówka, przeciągnie dzielnika między elementami itd.

Komunikaty powiadomień skojarzone z kontrolką nagłówka są wymienione w temacie [Informacje o formancie nagłówka](/windows/win32/controls/header-control-reference) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](using-cheaderctrl.md)<br/>
[Formanty](controls-mfc.md)

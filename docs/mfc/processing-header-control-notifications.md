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
ms.openlocfilehash: 42113b43249b87a351047ab451cb1798aec1f022
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693350"
---
# <a name="processing-header-control-notifications"></a>Przetwarzanie powiadomień dotyczących formantu karty

W klasie widoku lub w oknie dialogowym, użyj okna właściwości, aby utworzyć [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi za pomocą instrukcji switch dla każdego formantu nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) komunikaty powiadomień, które mają być Obsługa (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)). Powiadomienia są wysyłane do okna nadrzędnego, gdy użytkownik kliknie przycisk lub kliknie dwukrotnie element nagłówka drags na linię podziału między elementami i tak dalej.

Powiadomienia związane z formantem nagłówka są wymienione w [odwołanie do formantu nagłówka](/windows/desktop/controls/header-control-reference) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)


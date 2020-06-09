---
title: Obsługa komunikatów odbitych
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 8907b432cf4dabad33c0925b841f65dfc57c6295
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620138"
---
# <a name="handling-reflected-messages"></a>Obsługa komunikatów odbitych

Odbicie komunikatów umożliwia obsługę komunikatów dla kontrolki, takich jak **WM_CTLCOLOR**, **WM_COMMAND**i **WM_NOTIFY**, w obrębie formantu. Powoduje to, że formant jest bardziej niezależny i przenośny. Mechanizm działa z typowymi kontrolkami systemu Windows, a także z kontrolkami ActiveX (wcześniej nazywanymi kontrolkami OLE).

Odbicie komunikatów pozwala łatwiej ponownie wykorzystać `CWnd` klasy pochodne. Odbicie komunikatów działa za pośrednictwem [CWnd:: OnChildNotify](reference/cwnd-class.md#onchildnotify), przy użyciu specjalnych wpisów mapy komunikatów **ON_XXX_REFLECT** : na przykład **ON_CTLCOLOR_REFLECT** i **ON_CONTROL_REFLECT**. [Uwaga techniczna 62](tn062-message-reflection-for-windows-controls.md) wyjaśnia odbicie komunikatów bardziej szczegółowo.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

- [Dowiedz się więcej o odbiciu komunikatów](tn062-message-reflection-for-windows-controls.md)

- [Implementuj odbicie komunikatu dla wspólnej kontrolki](tn062-message-reflection-for-windows-controls.md)

- [Implementuj odbicie komunikatu dla kontrolki ActiveX](mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>Zobacz też

[Deklarowanie funkcji obsługi komunikatów](declaring-message-handler-functions.md)

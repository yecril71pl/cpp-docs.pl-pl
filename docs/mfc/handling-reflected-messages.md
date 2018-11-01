---
title: Obsługa komunikatów odbitych
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 9b580c0c8b8fc970d69f5c57f69bbbbe65e22497
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449871"
---
# <a name="handling-reflected-messages"></a>Obsługa komunikatów odbitych

Odbicie umożliwia obsługi wiadomości dla kontrolki, takie jak wiadomości **wm_ctlcolor —**, **WM_COMMAND**, i **WM_NOTIFY**, bezpośrednio w formancie. To sprawia, że kontrolka bardziej niezależną i przenośną. Mechanizm współpracuje ze wspólnych formantów Windows, a także z kontrolkami ActiveX (dawniej nazywanych formantów OLE).

Odbicie umożliwia ponowne używanie wiadomości usługi `CWnd`-klasy pochodne łatwiej. Komunikat odbicia działa za pośrednictwem [CWnd::OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify), za pomocą specjalnych **ON_XXX_REFLECT** wpisy mapy komunikatów: na przykład **ON_CTLCOLOR_REFLECT** i **ON_CONTROL_REFLECT**. [Techniczne 62 Uwaga](../mfc/tn062-message-reflection-for-windows-controls.md) opisano odbicie komunikatu bardziej szczegółowo.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

- [Dowiedz się więcej o odbicie komunikatu](../mfc/tn062-message-reflection-for-windows-controls.md)

- [Odbicie komunikatu dla formantu typowego wdrożenia](../mfc/tn062-message-reflection-for-windows-controls.md)

- [Implementowanie odbicie komunikatu dla formantów ActiveX](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>Zobacz też

[Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)

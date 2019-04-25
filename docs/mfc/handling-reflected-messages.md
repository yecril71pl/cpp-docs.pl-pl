---
title: Obsługa komunikatów odbitych
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 973e8cff24eca37b1806207d081636f0d1b38365
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240564"
---
# <a name="handling-reflected-messages"></a>Obsługa komunikatów odbitych

Odbicie umożliwia obsługi wiadomości dla kontrolki, takie jak wiadomości **wm_ctlcolor —**, **WM_COMMAND**, i **WM_NOTIFY**, bezpośrednio w formancie. To sprawia, że kontrolka bardziej niezależną i przenośną. Mechanizm współpracuje ze wspólnych formantów Windows, a także z kontrolkami ActiveX (dawniej nazywanych formantów OLE).

Odbicie umożliwia ponowne używanie wiadomości usługi `CWnd`-klasy pochodne łatwiej. Komunikat odbicia działa za pośrednictwem [CWnd::OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify), za pomocą specjalnych **ON_XXX_REFLECT** wpisy mapy komunikatów: na przykład **ON_CTLCOLOR_REFLECT** i **ON_CONTROL_REFLECT**. [Techniczne 62 Uwaga](../mfc/tn062-message-reflection-for-windows-controls.md) opisano odbicie komunikatu bardziej szczegółowo.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

- [Dowiedz się więcej o odbicie komunikatu](../mfc/tn062-message-reflection-for-windows-controls.md)

- [Odbicie komunikatu dla formantu typowego wdrożenia](../mfc/tn062-message-reflection-for-windows-controls.md)

- [Implementowanie odbicie komunikatu dla formantów ActiveX](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>Zobacz także

[Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)

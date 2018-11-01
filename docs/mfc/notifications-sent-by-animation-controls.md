---
title: Powiadomienia wysyłane przez formanty animacji
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 8c437e6950435b49c280c4f1bb9225002545d6f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449299"
---
# <a name="notifications-sent-by-animation-controls"></a>Powiadomienia wysyłane przez formanty animacji

Formantu animacji ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) wysyła dwa różne typy komunikatów powiadomień. Powiadomienia są wysyłane w postaci [WM_COMMAND](/windows/desktop/menurc/wm-command) wiadomości.

[ACN_START](/windows/desktop/Controls/acn-start) wiadomość jest wysyłana, gdy kontrolki animacji rozpoczęto odtwarzanie klipu. [ACN_STOP](/windows/desktop/Controls/acn-stop) wiadomość jest wysyłana, gdy kontrolki animacji ma zostało zakończone lub zatrzymać odtwarzanie klipu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)


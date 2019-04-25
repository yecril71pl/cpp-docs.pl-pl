---
title: Powiadomienia wysyłane przez formanty animacji
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 2a736e4315091b1b26daceb4fe0ce9672ab33ff6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62238312"
---
# <a name="notifications-sent-by-animation-controls"></a>Powiadomienia wysyłane przez formanty animacji

Formantu animacji ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) wysyła dwa różne typy komunikatów powiadomień. Powiadomienia są wysyłane w postaci [WM_COMMAND](/windows/desktop/menurc/wm-command) wiadomości.

[ACN_START](/windows/desktop/Controls/acn-start) wiadomość jest wysyłana, gdy kontrolki animacji rozpoczęto odtwarzanie klipu. [ACN_STOP](/windows/desktop/Controls/acn-stop) wiadomość jest wysyłana, gdy kontrolki animacji ma zostało zakończone lub zatrzymać odtwarzanie klipu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

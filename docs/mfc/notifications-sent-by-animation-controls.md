---
title: Powiadomienia wysyłane przez formanty animacji
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: e9e5b94736de44d5cfeef81f5b78a759df3b8aa0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619908"
---
# <a name="notifications-sent-by-animation-controls"></a>Powiadomienia wysyłane przez formanty animacji

Kontrolka animacji ([Korzystanie CAnimateCtrl](reference/canimatectrl-class.md)) wysyła dwa różne typy komunikatów powiadomień. Powiadomienia są wysyłane w formie [WM_COMMAND](/windows/win32/menurc/wm-command) komunikatów.

Komunikat [ACN_START](/windows/win32/Controls/acn-start) jest wysyłany po rozpoczęciu odtwarzania klipu przez kontrolkę animacji. Komunikat [ACN_STOP](/windows/win32/Controls/acn-stop) jest wysyłany po zakończeniu lub zatrzymaniu odtwarzania klipu przez kontrolkę animacji.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CAnimateCtrl](using-canimatectrl.md)<br/>
[Formanty](controls-mfc.md)

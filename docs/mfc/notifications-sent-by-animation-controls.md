---
title: Powiadomienia wysyłane przez formanty animacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb83fe6195c01c1e9dbcc2c00e43738af9ebc8e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386395"
---
# <a name="notifications-sent-by-animation-controls"></a>Powiadomienia wysyłane przez formanty animacji

Formantu animacji ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) wysyła dwa różne typy komunikatów powiadomień. Powiadomienia są wysyłane w postaci [WM_COMMAND](/windows/desktop/menurc/wm-command) wiadomości.

[ACN_START](/windows/desktop/Controls/acn-start) wiadomość jest wysyłana, gdy kontrolki animacji rozpoczęto odtwarzanie klipu. [ACN_STOP](/windows/desktop/Controls/acn-stop) wiadomość jest wysyłana, gdy kontrolki animacji ma zostało zakończone lub zatrzymać odtwarzanie klipu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)


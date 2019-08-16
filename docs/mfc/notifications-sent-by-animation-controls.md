---
title: Powiadomienia wysyłane przez formanty animacji
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 68ede3bc55669a29eef192d38b29b8c1ab433e4b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508015"
---
# <a name="notifications-sent-by-animation-controls"></a>Powiadomienia wysyłane przez formanty animacji

Kontrolka animacji ([Korzystanie CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) wysyła dwa różne typy komunikatów powiadomień. Powiadomienia są wysyłane w formie komunikatów [WM_COMMAND](/windows/win32/menurc/wm-command) .

Komunikat [ACN_START](/windows/win32/Controls/acn-start) jest wysyłany po rozpoczęciu odtwarzania klipu przez kontrolkę animacji. Komunikat [ACN_STOP](/windows/win32/Controls/acn-stop) jest wysyłany po zakończeniu lub zatrzymaniu odtwarzania klipu przez kontrolkę animacji.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

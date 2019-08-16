---
title: Klawisze dostępu właściwe dla wątków
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 49bac6ac357924c26f131bbd8e1092cd74514167
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511141"
---
# <a name="thread-specific-hot-keys"></a>Klawisze dostępu właściwe dla wątków

Aplikacja ustawia klawisz dostępu specyficzny dla wątku ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) przy użyciu funkcji systemu Windows `RegisterHotKey` . Gdy użytkownik naciśnie klawisz dostępu specyficzny dla wątku, system Windows ogłasza komunikat [WM_HOTKEY](/windows/win32/inputdev/wm-hotkey) na początku kolejki komunikatów określonego wątku. Komunikat WM_HOTKEY zawiera kod klucza wirtualnego, stan przesunięcia i zdefiniowany przez użytkownika identyfikator określonego klawisza skrótu, który został naciśnięty. Aby uzyskać listę standardowych kodów kluczy wirtualnych, zobacz Winuser. h. Aby uzyskać więcej informacji na temat tej metody, zobacz [funkcję RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey).

Należy zauważyć, że flagi zmiany stanu użyte w wywołaniu `RegisterHotKey` nie są takie same jak te zwrócone przez funkcję członkowską GetHotKey; przed wywołaniem [](../mfc/reference/chotkeyctrl-class.md#gethotkey) `RegisterHotKey`należy przetłumaczyć te flagi.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

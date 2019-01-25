---
title: Klawisze dostępu właściwe dla wątków
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 68c50ec5f29dab271f9af9abc50eb72ec15157e7
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893330"
---
# <a name="thread-specific-hot-keys"></a>Klawisze dostępu właściwe dla wątków

Aplikacja ustawia klawisza dostępu właściwe dla wątków ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) przy użyciu Windows `RegisterHotKey` funkcji. Gdy użytkownik naciśnie klawisz dostępu właściwe dla wątków, publikuje Windows [WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey) wiadomości na początek kolejki komunikatów określonego wątku. Komunikat WM_HOTKEY zawiera wirtualny kod klawisza, stan shift i zdefiniowanych przez użytkownika identyfikator określonego klawisza dostępu, który został naciśnięty. Aby uzyskać listę standardowa wirtualnej kody klawiszy Zobacz Winuser.h. Aby uzyskać więcej informacji na temat tej metody, zobacz [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey).

Należy zauważyć, że flagi stanu shift używane w wywołaniu `RegisterHotKey` nie są takie same, jak zwracany przez [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) funkcję członkowską; musisz tłumaczenie tych flag przed wywołaniem `RegisterHotKey`.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)


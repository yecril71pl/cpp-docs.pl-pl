---
title: Klawisze dostępu właściwe dla wątków
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: a54aa878b0160132157879127f8335c951e91785
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290992"
---
# <a name="thread-specific-hot-keys"></a>Klawisze dostępu właściwe dla wątków

Aplikacja ustawia klawisza dostępu właściwe dla wątków ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) przy użyciu Windows `RegisterHotKey` funkcji. Gdy użytkownik naciśnie klawisz dostępu właściwe dla wątków, publikuje Windows [WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey) wiadomości na początek kolejki komunikatów określonego wątku. Komunikat WM_HOTKEY zawiera wirtualny kod klawisza, stan shift i zdefiniowanych przez użytkownika identyfikator określonego klawisza dostępu, który został naciśnięty. Aby uzyskać listę standardowa wirtualnej kody klawiszy Zobacz Winuser.h. Aby uzyskać więcej informacji na temat tej metody, zobacz [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey).

Należy zauważyć, że flagi stanu shift używane w wywołaniu `RegisterHotKey` nie są takie same, jak zwracany przez [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) funkcję członkowską; musisz tłumaczenie tych flag przed wywołaniem `RegisterHotKey`.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

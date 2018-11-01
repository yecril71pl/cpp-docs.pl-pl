---
title: Klawisze dostępu właściwe dla wątków
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 4b393fe1af060a4b235162ce8cdfd94a1a391085
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594158"
---
# <a name="thread-specific-hot-keys"></a>Klawisze dostępu właściwe dla wątków

Aplikacja ustawia klawisza dostępu właściwe dla wątków ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) przy użyciu Windows `RegisterHotKey` funkcji. Gdy użytkownik naciśnie klawisz dostępu właściwe dla wątków, publikuje Windows [WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey) wiadomości na początek kolejki komunikatów określonego wątku. Komunikat WM_HOTKEY zawiera wirtualny kod klawisza, stan shift i zdefiniowanych przez użytkownika identyfikator określonego klawisza dostępu, który został naciśnięty. Aby uzyskać listę standardowa wirtualnej kody klawiszy Zobacz Winuser.h. Aby uzyskać więcej informacji na temat tej metody, zobacz [RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309).

Należy zauważyć, że flagi stanu shift używane w wywołaniu `RegisterHotKey` nie są takie same, jak zwracany przez [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) funkcję członkowską; musisz tłumaczenie tych flag przed wywołaniem `RegisterHotKey`.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)


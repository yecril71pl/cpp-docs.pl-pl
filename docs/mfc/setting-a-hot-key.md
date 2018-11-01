---
title: Ustawianie klawisza dostępu
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: a5dc885767137a4e53d1ea0d066944d5f276c38c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508800"
---
# <a name="setting-a-hot-key"></a>Ustawianie klawisza dostępu

Aplikacja może użyć informacji dostarczonych przez klawisza dostępu ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) kontrolki w jeden z dwóch sposobów:

- Konfigurowanie globalny klawisz dostępu do aktywacji okna nonchild, wysyłając [WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) komunikat w oknie zostanie uaktywniony.

- Ustawianie klawisza dostępu właściwe dla wątków, wywołując funkcję Windows [RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)


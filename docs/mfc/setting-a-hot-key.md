---
title: Ustawianie klawisza dostępu
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: a77aad4881acd04c6dabb6dce90acc01be2cfbc8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281281"
---
# <a name="setting-a-hot-key"></a>Ustawianie klawisza dostępu

Aplikacja może użyć informacji dostarczonych przez klawisza dostępu ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) kontrolki w jeden z dwóch sposobów:

- Konfigurowanie globalny klawisz dostępu do aktywacji okna nonchild, wysyłając [WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) komunikat w oknie zostanie uaktywniony.

- Ustawianie klawisza dostępu właściwe dla wątków, wywołując funkcję Windows [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey).

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

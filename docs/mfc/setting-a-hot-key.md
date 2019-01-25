---
title: Ustawianie klawisza dostępu
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: ebaddb4a64a4d9d47b82fd36f118c74527554e53
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893227"
---
# <a name="setting-a-hot-key"></a>Ustawianie klawisza dostępu

Aplikacja może użyć informacji dostarczonych przez klawisza dostępu ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) kontrolki w jeden z dwóch sposobów:

- Konfigurowanie globalny klawisz dostępu do aktywacji okna nonchild, wysyłając [WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) komunikat w oknie zostanie uaktywniony.

- Ustawianie klawisza dostępu właściwe dla wątków, wywołując funkcję Windows [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)


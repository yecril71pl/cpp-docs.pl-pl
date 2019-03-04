---
title: Globalne klawisze dostępu
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: eedeb0547320c8b421fa72647f51b02f834af300
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273633"
---
# <a name="global-hot-keys"></a>Globalne klawisze dostępu

Globalny klawisz dostępu jest skojarzony z oknem nonchild określonej. Umożliwia użytkownikowi Uaktywnij okno z dowolnej części systemu. Aplikacja ustawia globalny klawisz dostępu określonego okna, wysyłając [WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) komunikat do tego okna. Na przykład jeśli `m_HotKeyCtrl` jest [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) obiektu i `pMainWnd` jest wskaźnikiem do okna, który będzie aktywowany po naciśnięciu klawisza dostępu, można Użyj poniższego kodu, aby skojarzyć klawisz dostępu określonego w kontrolki z Okno wskazywany przez `pMainWnd`.

[!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]

Zawsze, gdy użytkownik naciśnie globalny klawisz dostępu, określone okno odbiera [WM_SYSCOMMAND](/windows/desktop/menurc/wm-syscommand) komunikat, który określa **SC_HOTKEY** jako typ polecenia. Ten komunikat aktywuje również okno, które otrzymuje go. Ponieważ ten komunikat nie zawiera żadnych informacji na temat dokładnego klucza, który został naciśnięty, przy użyciu tej metody nie zezwala na rozróżniania różne klawisze dostępu, które mogą być dołączone do tego samego okna. Klawisz skrótu pozostanie ważny aż do aplikacji, która wysłała **WM_SETHOTKEY** kończy działanie.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

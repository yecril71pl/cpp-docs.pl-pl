---
title: Inicjowanie części obiektu CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: a5b65a2bbb68eaa7058f3514bb95a5209a0e5e71
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444450"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Inicjowanie części obiektu CStatusBarCtrl

Domyślnie pasek stanu wyświetla informacje o stanie przy użyciu oddzielnych okienek. Te okienka (nazywane również częścią) mogą zawierać ciąg tekstowy, ikonę lub obie te okna.

Użyj elementu [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) , aby zdefiniować, ile części i długości ma mieć pasek stanu. Po utworzeniu części paska stanu, wykonaj wywołania do [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) i [SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon) , aby ustawić tekst lub ikonę dla określonej części paska stanu. Po pomyślnym ustawieniu części kontrolka zostanie automatycznie narysowana ponownie.

Poniższy przykład inicjuje istniejący obiekt `CStatusBarCtrl` (`m_StatusBarCtrl`) z czterema okienkami, a następnie ustawia ikonę (IDI_ICON1) i tekst w drugiej części.

[!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

Aby uzyskać więcej informacji na temat ustawiania trybu obiektu `CStatusBarCtrl` na prosty, zobacz [Ustawianie trybu obiektu CStatusBarCtrl](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

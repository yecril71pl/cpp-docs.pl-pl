---
title: Inicjowanie części obiektu CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: 0f00aee03a74799bf14563653b50c487ff001d02
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182322"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Inicjowanie części obiektu CStatusBarCtrl

Domyślnie pasek stanu wyświetla informacje o stanie przy użyciu oddzielnych okienek. Te okienka (określane również jako części) może zawierać ciąg tekstowy, ikony lub obu.

Użyj [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) określenie, ile części i długość, będzie miał na pasku stanu. Po utworzeniu części paska stanu wykonywania wywołań do [SetText —](../mfc/reference/cstatusbarctrl-class.md#settext) i [SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon) można ustawić tekst lub ikonę dla określonej części na pasku stanu. Po pomyślnym ustawieniu część automatycznie odświeżeniu formantu.

Poniższy przykład inicjuje istniejące `CStatusBarCtrl` obiektu (`m_StatusBarCtrl`) z czterech okienka, a następnie ustawia ikonę (IDI_ICON1) i tekst w drugiej części.

[!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

Aby uzyskać więcej informacji na temat ustawiania trybu `CStatusBarCtrl` obiektu do prostego, zobacz [Ustawianie trybu obiektu CStatusBarCtrl](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

## <a name="see-also"></a>Zobacz także

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

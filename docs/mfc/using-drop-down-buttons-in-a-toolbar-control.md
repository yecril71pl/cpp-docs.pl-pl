---
title: Używanie przycisków listy rozwijanej w formancie paska narzędzi
ms.date: 11/04/2016
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
ms.openlocfilehash: 0bc4df4c07ec4b8bc5b488925cbb140609302186
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365068"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Używanie przycisków listy rozwijanej w formancie paska narzędzi

Oprócz standardowych przycisków pasek narzędzi może mieć również przyciski rozwijane. Przycisk rozwijany jest zwykle wskazywany przez obecność dołączonej strzałki w dół.

> [!NOTE]
> Dołączona strzałka w dół pojawi się tylko wtedy, gdy ustawiono TBSTYLE_EX_DRAWDDARROWS styl rozszerzony.

Gdy użytkownik kliknie tę strzałkę (lub sam przycisk, jeśli nie ma strzałki), do rodzica formantu paska narzędzi zostanie wysłana wiadomość z powiadomieniem TBN_DROPDOWN. Następnie można obsłużyć to powiadomienie i wyświetlić menu podręczne; podobne do zachowania programu Internet Explorer.

Poniższa procedura ilustruje sposób zaimplementowania przycisku rozwijanego paska narzędzi z wyskakującym menu:

### <a name="to-implement-a-drop-down-button"></a>Aby zaimplementować przycisk listy rozwijanej

1. Po `CToolBarCtrl` utworzeniu obiektu ustaw styl TBSTYLE_EX_DRAWDDARROWS, używając następującego kodu:

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. Ustaw styl TBSTYLE_DROPDOWN dla dowolnych nowych[(InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) lub [AddButtons)](../mfc/reference/ctoolbarctrl-class.md#addbuttons)lub istniejących[(SetButtonInfo),](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)które będą przyciskami rozwijaną. Poniższy przykład pokazuje modyfikowanie istniejącego `CToolBarCtrl` przycisku w obiekcie:

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. Dodaj program obsługi TBN_DROPDOWN do klasy nadrzędnej obiektu paska narzędzi.

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. W nowym programie obsługi wyświetl odpowiednie menu podręczne. Poniższy kod demonstruje jedną metodę:

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)

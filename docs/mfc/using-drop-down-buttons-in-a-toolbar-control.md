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
ms.openlocfilehash: 8d1a13b1921f111d97bb515e7932a0116277f9ed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411607"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Używanie przycisków listy rozwijanej w formancie paska narzędzi

Oprócz standardowych przycisków pasek narzędzi może być również przycisków listy rozwijanej. Przycisk listy rozwijanej zwykle jest wskazywane przez obecność Strzałka dołączone w dół.

> [!NOTE]
>  Dołączone w dół strzałki będą wyświetlane tylko wtedy, gdy ustawiono TBSTYLE_EX_DRAWDDARROWS rozszerzone style.

Gdy użytkownik kliknie ten strzałka (lub przycisk, jeśli ma nie strzałkę), tbn_dropdown — powiadomienie jest wysyłane do nadrzędnego formantu paska narzędzi. Można obsługiwać to powiadomienie i wyświetlanie wyskakujących menu. podobne do zachowania programu Internet Explorer.

Poniższa procedura ilustruje sposób implementacji przycisk rozwijany pasek narzędzi z menu podręcznego:

### <a name="to-implement-a-drop-down-button"></a>Aby zaimplementować przycisk listy rozwijanej

1. Gdy Twoja `CToolBarCtrl` obiekt został utworzony, ustaw styl TBSTYLE_EX_DRAWDDARROWS, używając następującego kodu:

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. Ustaw styl TBSTYLE_DROPDOWN dla każdego nowego ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) lub [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) lub istniejące ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) przyciski, który ma być przycisków listy rozwijanej. W poniższym przykładzie pokazano, modyfikowania istniejących przycisk `CToolBarCtrl` obiektu:

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. Dodawanie obsługi tbn_dropdown — do klasy nadrzędnej obiektu paska narzędzi.

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. W obsłudze nowe wyświetlane menu podręczne odpowiednie. Poniższy kod przedstawia jedną z metod:

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>Zobacz także

[Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

---
title: Używanie przycisków listy rozwijanej w formancie paska narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
dev_langs:
- C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e76db0bacd7984c97fd8e2696b3543f6e9bf66b
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953246"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Używanie przycisków listy rozwijanej w formancie paska narzędzi
Oprócz standardowych przycisków pasek narzędzi może zawierać również przycisków listy rozwijanej. Obecność dołączone klawisz Strzałka zwykle wskazuje przycisku rozwijanego.  
  
> [!NOTE]
>  Dołączone klawisz Strzałka będą wyświetlane tylko wtedy, gdy ustawiono TBSTYLE_EX_DRAWDDARROWS rozszerzone style.  
  
 Gdy użytkownik kliknie ten strzałka (lub przycisk, jeśli strzałkę nie jest obecny), tbn_dropdown — powiadomienie jest wysyłane do nadrzędnego formantu paska narzędzi. Można obsłużyć tego powiadomienia i wyświetlenia menu podręcznego; podobne do zachowania programu Internet Explorer.  
  
 Poniższa procedura ilustruje sposób implementowania przycisku paska narzędzi z listy rozwijanej z menu podręczne:  
  
### <a name="to-implement-a-drop-down-button"></a>Aby zaimplementować przycisku rozwijanego  
  
1.  Raz z `CToolBarCtrl` obiekt został utworzony, ustawienie stylu TBSTYLE_EX_DRAWDDARROWS, używając następującego kodu:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]  
  
2.  Ustawienie stylu TBSTYLE_DROPDOWN dla każdego nowego ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) lub [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) lub istniejące ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) przycisków, który ma być przycisków listy rozwijanej. W poniższym przykładzie pokazano modyfikowanie istniejącego przycisku w `CToolBarCtrl` obiektu:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]  
  
3.  Dodaj program obsługi tbn_dropdown — do klasy nadrzędnej obiektu paska narzędzi.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]  
  
4.  W nowy program obsługi wyświetlanie menu podręcznego odpowiednie. Poniższy kod przedstawia jedną metodę:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)


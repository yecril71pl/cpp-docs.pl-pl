---
title: "Używanie przycisków listy rozwijanej w formancie paska narzędzi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
dev_langs: C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 01c09cb2bec4b466928557434767ce49948f46ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Używanie przycisków listy rozwijanej w formancie paska narzędzi
Oprócz standardowych przycisków pasek narzędzi może zawierać również przycisków listy rozwijanej. Obecność dołączone klawisz Strzałka zwykle wskazuje przycisku rozwijanego.  
  
> [!NOTE]
>  Dołączone klawisz Strzałka pojawi się tylko wtedy, gdy `TBSTYLE_EX_DRAWDDARROWS` rozszerzonego stylu została ustawiona.  
  
 Gdy użytkownik kliknie ta strzałka (lub sam, jeśli nie strzałkę znajduje się przycisk) `TBN_DROPDOWN` powiadomienie jest wysyłane do nadrzędnego formantu paska narzędzi. Można obsłużyć tego powiadomienia i wyświetlenia menu podręcznego; podobne do zachowania programu Internet Explorer.  
  
 Poniższa procedura ilustruje sposób implementowania przycisku paska narzędzi z listy rozwijanej z menu podręczne:  
  
### <a name="to-implement-a-drop-down-button"></a>Aby zaimplementować przycisku rozwijanego  
  
1.  Raz z `CToolBarCtrl` obiekt został utworzony, ustaw `TBSTYLE_EX_DRAWDDARROWS` styl, używając następującego kodu:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]  
  
2.  Ustaw `TBSTYLE_DROPDOWN` stylu dla każdego nowego ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) lub [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) lub istniejące ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) przycisków, który ma być przycisków listy rozwijanej. W poniższym przykładzie pokazano modyfikowanie istniejącego przycisku w `CToolBarCtrl` obiektu:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]  
  
3.  Dodaj `TBN_DROPDOWN` obsługi do klasy nadrzędnej obiektu paska narzędzi.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]  
  
4.  W nowy program obsługi wyświetlanie menu podręcznego odpowiednie. Poniższy kod przedstawia jedną metodę:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)


---
title: Operowanie formantem etykietki narzędzia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76976c0907d645ad945700c4d396217880712f11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="manipulating-the-tool-tip-control"></a>Operowanie formantem etykietki narzędzia
Klasa `CToolTipCtrl` udostępnia funkcje kontrolować różne atrybuty elementu członkowskiego grupy `CToolTipCtrl` obiekt i Porada okna narzędzia.  
  
 Początkowy, w oknie podręcznym i reshow czasu trwania dla narzędzia windows Porada można ustawić i pobierane z wywołaniami [GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime) i [SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime).  
  
 Zmienianie wyglądu narzędzia windows tip z następujących funkcji:  
  
-   [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin) i [SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin) pobiera i ustawia odstęp między obramowania Porada narzędzia i narzędzie Tekst porady.  
  
-   [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth) i [SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth) pobiera i ustawia maksymalną szerokość narzędzia Porada okna.  
  
-   [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor) i [SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor) pobiera i ustawia kolor tła narzędzia Porada okna.  
  
-   [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor) i [SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor) pobiera i ustawia kolor tekstu narzędzia Porada okna.  
  
 Aby formantem etykietki narzędzia ma być powiadamiany o ważne komunikaty, takie jak **WM_LBUTTONXXX** wiadomości, przekazywania wiadomości z formantem etykietki narzędzia. Jest najlepszą metodę dla tego przekazywania do wywoływania [CToolTipCtrl::RelayEvent](../mfc/reference/ctooltipctrl-class.md#relayevent)w `PreTranslateMessage` funkcja okno właściciela. Poniższy przykład przedstawia jedną z możliwych metod (przy założeniu formantem etykietki narzędzia jest nazywany `m_ToolTip`):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]  
  
 Aby natychmiast usunąć okna Porada narzędzia, należy wywołać [Pop](../mfc/reference/ctooltipctrl-class.md#pop) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)


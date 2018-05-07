---
title: Metody tworzenia etykietek narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26f6e7cbf8c6464afa90c52f9cd91dcdb55de767
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="methods-of-creating-tool-tips"></a>Metody tworzenia etykietek narzędzi
MFC udostępnia trzy klasy Tworzenie i zarządzanie nimi narzędzie formantu etykietki: [CWnd](../mfc/reference/cwnd-class.md), [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md), [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) i [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md). Funkcje Członkowskie Porada narzędzia w tych klas zawijanie formantu wspólnego interfejsu API systemu Windows. Klasa `CToolBarCtrl` i klasa `CToolTipCtrl` są pochodnymi klasy `CWnd`.  
  
 `CWnd` udostępnia cztery funkcje Członkowskie tworzenie i zarządzanie nimi etykietki narzędzi: [EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips), [CancelToolTips](../mfc/reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](../mfc/reference/cwnd-class.md#filtertooltipmessage), i [OnToolHitTest ](../mfc/reference/cwnd-class.md#ontoolhittest). Zobacz te funkcje poszczególnych elementów członkowskich, aby uzyskać więcej informacji na temat sposobu wdrażania etykietek narzędzi.  
  
 W przypadku utworzenia przy użyciu narzędzi `CToolBarCtrl`, można zaimplementować etykietki narzędzi dla tego paska narzędzi bezpośrednio przy użyciu następujących funkcji elementów członkowskich: [GetToolTips](../mfc/reference/ctoolbarctrl-class.md#gettooltips) i [SetToolTips](../mfc/reference/ctoolbarctrl-class.md#settooltips). Zobacz te funkcje poszczególnych elementów członkowskich i [Obsługa powiadomień dotyczących Porada narzędzi](../mfc/handling-tool-tip-notifications.md) uzyskać więcej informacji dotyczących sposobu wdrażania etykietek narzędzi.  
  
 `CToolTipCtrl` Klasa udostępnia funkcje formantem etykietki narzędzia wspólne systemu Windows. Formantem etykietki narzędzia pojedynczego zapewniają informacje o więcej niż jedno narzędzie. To narzędzie jest albo okna, takich jak kontrolki lub okna podrzędnego albo zdefiniowanym przez aplikację prostokątny obszar wewnątrz obszaru klienckiego okna. [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md) pochodną klasy `CToolTipCtrl` i udostępnia dodatkowe stylów wizualnych i możliwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)


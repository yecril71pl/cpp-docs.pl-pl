---
title: Dostosowywanie wyglądu formantu paska narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBSTYLE_
dev_langs:
- C++
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54c512bd727b7ef36ee94eb5ccaf3018be692d14
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197698"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Dostosowywanie wyglądu formantu paska narzędzi
Klasa `CToolBarCtrl` udostępnia wiele style, które mają wpływ na wygląd (a czasami zachowanie) obiektu paska narzędzi. Zmodyfikować obiekt paska narzędzi, ustawiając `dwCtrlStyle` parametru `CToolBarCtrl::Create` (lub `CToolBar::CreateEx`) funkcja elementu członkowskiego, podczas pierwszego tworzenia formantu paska narzędzi.  
  
 Następujące style wpływają na aspekt "3D" przycisków paska narzędzi i rozmieszczenie tekstu przycisku:  
  
-   **TBSTYLE_FLAT** tworzy prostych narzędzi, gdzie zarówno w pasku narzędzi, jak i przyciski są niewidoczne. Tekst przycisku zostanie wyświetlone w obszarze mapy bitowe przycisków. Gdy używany jest ten styl, przycisk poniżej kursora automatycznie zostanie wyróżniona.  
  
-   **TBSTYLE_TRANSPARENT** tworzy przezroczyste paska narzędzi. Przezroczysty pasku narzędzi pasek narzędzi jest niewidoczny, ale są przyciski. Tekst przycisku zostanie wyświetlone w obszarze mapy bitowe przycisków.  
  
-   **TBSTYLE_LIST** miejsc przycisku tekstu z prawej strony mapy bitowe przycisków.  
  
> [!NOTE]
>  Aby uniknąć problemów z repaint **TBSTYLE_FLAT** i **TBSTYLE_TRANSPARENT** style powinna być ustawiona, zanim obiekt paska narzędzi jest widoczny.  
  
 Następujące style określają umożliwia użytkownikowi zmienianie położenia poszczególnych przycisków w obiekcie narzędzi przy użyciu przeciągania i upuszczania, jeśli pasek narzędzi:  
  
-   **TBSTYLE_ALTDRAG** umożliwia użytkownikom zmianę pozycji przycisku paska narzędzi, przeciągając go, przytrzymując naciśnięty klawisz ALT. Jeśli ten styl nie zostanie określony, użytkownik musi przytrzymaj wciśnięty klawisz SHIFT podczas przeciągania przycisku.  
  
    > [!NOTE]
    >  **CCS_ADJUSTABLE** stylu muszą określać umożliwiające można przeciągnąć przyciski paska narzędzi.  
  
-   **TBSTYLE_REGISTERDROP** generuje **TBN_GETOBJECT** powiadomień wiadomości, aby zażądać porzucić obiektów docelowych, gdy wskaźnik myszy przesuwa się nad przycisków paska narzędzi.  
  
 Pozostałe style wpływają na visual Niewizualne aspekty i obiekt paska narzędzi:  
  
-   **TBSTYLE_WRAPABLE** tworzy pasek narzędzi, który może mieć wiele wierszy przycisków. Przyciski paska narzędzi można "opakować" do następnego wiersza po pasku narzędzi staje się zbyt wąska, aby uwzględnić wszystkie przyciski, w tym samym wierszu. OPAKOWYWANIE odbywa się na rozdzielenie i nongroup granic.  
  
-   **TBSTYLE_CUSTOMERASE** generuje **NM_CUSTOMDRAW** komunikaty powiadomień podczas przetwarzania **WM_ERASEBKGND** wiadomości.  
  
-   **TBSTYLE_TOOLTIPS** tworzy formantem etykietki narzędzia, które aplikacja może użyć, aby wyświetlić tekst opisu dla przycisków na pasku narzędzi.  
  
 Aby uzyskać pełną listę toolbar — style i rozszerzone style, zobacz [formantu paska narzędzi oraz style przycisku](/windows/desktop/Controls/toolbar-control-and-button-styles) i [Toolbar — rozszerzone style](/windows/desktop/Controls/toolbar-extended-styles) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)


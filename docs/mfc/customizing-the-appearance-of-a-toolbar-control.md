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
ms.openlocfilehash: 48825a264b7d82152f47e70c5911bea400c313db
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932120"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Dostosowywanie wyglądu formantu paska narzędzi
Klasa `CToolBarCtrl` udostępnia wiele style, które wpływają na wygląd (i, czasami zachowanie) obiektu paska narzędzi. Zmodyfikuj obiekt paska narzędzi przez ustawienie `dwCtrlStyle` parametr `CToolBarCtrl::Create` (lub `CToolBar::CreateEx`) funkcji członkowskiej, podczas tworzenia formantu paska narzędzi.  
  
 Następujące style wpływać aspekt "3" przycisków paska narzędzi i rozmieszczenie tekst przycisku:  
  
-   **TBSTYLE_FLAT** tworzy płaskiej gdzie są niewidoczne zarówno pasek narzędzi i przycisków paska narzędzi. Tekst przycisku zostanie wyświetlone w obszarze mapy bitowe przycisków. Gdy używany jest ten styl, automatycznie zostanie wyróżniona przycisk pod kursorem.  
  
-   **TBSTYLE_TRANSPARENT** tworzy przezroczyste paska narzędzi. Przezroczysty pasku narzędzi pasek narzędzi jest niewidoczny, ale są przycisków. Tekst przycisku zostanie wyświetlone w obszarze mapy bitowe przycisków.  
  
-   **TBSTYLE_LIST** miejsca przycisk tekstu z prawej strony mapy bitowe przycisków.  
  
> [!NOTE]
>  Aby uniknąć problemów z odświeżenia **TBSTYLE_FLAT** i **TBSTYLE_TRANSPARENT** style powinien być ustawiony przed obiekt narzędzi jest widoczny.  
  
 Następujące style określają, jeśli pasek narzędzi umożliwia użytkownikowi zmienianie położenia poszczególnych przycisków w obiekcie paska narzędzi przez przeciąganie i upuszczanie:  
  
-   **TBSTYLE_ALTDRAG** umożliwia użytkownikom zmianę pozycji przycisku paska narzędzi, przeciągając go trzymając wciśnięty klawisz ALT. Jeśli nie określono tego stylu, użytkownik musi przytrzymaj klawisz SHIFT podczas przeciągania przycisku.  
  
    > [!NOTE]
    >  **CCS_ADJUSTABLE** styl należy określić umożliwiające przeciąganych przycisków paska narzędzi.  
  
-   **TBSTYLE_REGISTERDROP** generuje **TBN_GETOBJECT** powiadomień wiadomości, aby zażądać porzucić obiektów docelowych, gdy wskaźnik myszy przesuwa się nad przycisków paska narzędzi.  
  
 Pozostałe style wpływania na aspekty visual i niewidoczne obiektu narzędzi:  
  
-   **TBSTYLE_WRAPABLE** tworzy mające wiele wierszy przycisków paska narzędzi. Przyciski paska narzędzi można "wrap" do następnego wiersza po pasek narzędzi będzie zbyt ograniczone, aby uwzględnić wszystkie przyciski w tym samym wierszu. Zawijanie występuje na rozdzielenie i nongroup granic.  
  
-   **TBSTYLE_CUSTOMERASE** generuje **NM_CUSTOMDRAW** komunikatów powiadomień podczas przetwarzania **WM_ERASEBKGND** wiadomości.  
  
-   **TBSTYLE_TOOLTIPS** tworzy formantem etykietki narzędzia, która aplikacja może użyć do wyświetlenia opisu przycisków na pasku narzędzi.  
  
 Pełna lista Style paska narzędzi i rozszerzonej, zobacz [formantu paska narzędzi oraz style przycisku](http://msdn.microsoft.com/library/windows/desktop/bb760439) i [narzędzi rozszerzone style](http://msdn.microsoft.com/library/windows/desktop/bb760430) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)


---
title: Dostosowywanie wyglądu formantu paska narzędzi
ms.date: 11/04/2016
f1_keywords:
- TBSTYLE_
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
ms.openlocfilehash: 9f4f9d90113d5074555d1b0cc411f854abc67fe5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377461"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Dostosowywanie wyglądu formantu paska narzędzi

Klasa `CToolBarCtrl` zawiera wiele stylów, które wpływają na wygląd (i, od czasu do czasu, zachowanie) obiektu paska narzędzi. Zmodyfikuj obiekt `dwCtrlStyle` paska `CToolBarCtrl::Create` narzędzi, ustawiając parametr (lub) `CToolBar::CreateEx`funkcji elementu członkowskiego podczas pierwszego tworzenia formantu paska narzędzi.

Następujące style wpływają na aspekt "3D" przycisków paska narzędzi i położenie tekstu przycisku:

- **TBSTYLE_FLAT** Tworzy płaski pasek narzędzi, w którym zarówno pasek narzędzi, jak i przyciski są przezroczyste. Tekst przycisku pojawia się pod mapami bitowymi przycisków. Gdy ten styl jest używany, przycisk pod kursorem jest automatycznie podświetlany.

- **TBSTYLE_TRANSPARENT** Tworzy przezroczysty pasek narzędzi. Na przezroczystym pasku narzędzi pasek narzędzi jest przezroczysty, ale przyciski nie są. Tekst przycisku pojawia się pod mapami bitowymi przycisków.

- **TBSTYLE_LIST** Umieszcza tekst przycisku po prawej stronie map bitowych przycisków.

> [!NOTE]
> Aby zapobiec przemalowaniu problemów, style **TBSTYLE_FLAT** i **TBSTYLE_TRANSPARENT** powinny zostać ustawione przed widoczną obiekcie paska narzędzi.

Następujące style określają, czy pasek narzędzi umożliwia użytkownikowi zmianę położenia poszczególnych przycisków w obiekcie paska narzędzi za pomocą przeciągania i upuszczania:

- **TBSTYLE_ALTDRAG** Umożliwia użytkownikom zmianę położenia przycisku paska narzędzi, przeciągając go przy jednoczesnym przytrzymywaniem klawisza ALT. Jeśli ten styl nie jest określony, użytkownik musi przytrzymać klawisz SHIFT podczas przeciągania przycisku.

    > [!NOTE]
    >  Aby umożliwić przeciąganie przycisków paska narzędzi, należy określić styl **CCS_ADJUSTABLE.**

- **TBSTYLE_REGISTERDROP** Generuje **TBN_GETOBJECT** komunikatów powiadomień, aby zażądać upuszczenia obiektów docelowych, gdy wskaźnik myszy przechodzi nad przyciskami paska narzędzi.

Pozostałe style mają wpływ na wizualne i niewizualne aspekty obiektu paska narzędzi:

- **TBSTYLE_WRAPABLE** Tworzy pasek narzędzi, który może mieć wiele linii przycisków. Przyciski paska narzędzi mogą "zawijać" do następnego wiersza, gdy pasek narzędzi staje się zbyt wąski, aby uwzględnić wszystkie przyciski w tej samej linii. Zawijanie odbywa się na separacji i granic niegrupowych.

- **TBSTYLE_CUSTOMERASE** Generuje **NM_CUSTOMDRAW** wiadomości powiadomień podczas przetwarzania **WM_ERASEBKGND** wiadomości.

- **TBSTYLE_TOOLTIPS** Tworzy kontrolkę etykietki narzędzia, której aplikacja może używać do wyświetlania tekstu opisowego dla przycisków na pasku narzędzi.

Aby uzyskać pełną listę stylów paska narzędzi i stylów rozszerzonych, zobacz [Style formantów i przycisków paska narzędzi](/windows/win32/Controls/toolbar-control-and-button-styles) oraz [style rozszerzone paska narzędzi](/windows/win32/Controls/toolbar-extended-styles) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)

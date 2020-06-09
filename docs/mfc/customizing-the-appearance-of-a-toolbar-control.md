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
ms.openlocfilehash: ddccb5f05152d95377b430d7492ede3c86926e37
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619280"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Dostosowywanie wyglądu formantu paska narzędzi

Klasa `CToolBarCtrl` zawiera wiele stylów, które wpływają na wygląd obiektu Toolbar (i, przez czas, zachowanie). Zmodyfikuj obiekt Toolbar przez ustawienie `dwCtrlStyle` parametru `CToolBarCtrl::Create` `CToolBar::CreateEx` funkcji członkowskiej (lub), gdy tworzysz najpierw formant Toolbar.

Następujące style mają wpływ na aspekt "3W" przycisków paska narzędzi oraz umieszczanie tekstu przycisku:

- **TBSTYLE_FLAT** Tworzy płaski pasek narzędzi, w którym zarówno pasek narzędzi, jak i przyciski są przezroczyste. Tekst przycisku jest wyświetlany w obszarze mapy bitowe przycisków. Gdy ten styl jest używany, przycisk poniżej kursora zostanie automatycznie wyróżniony.

- **TBSTYLE_TRANSPARENT** Tworzy przezroczysty pasek narzędzi. Na przezroczystym pasku narzędzi pasek narzędzi jest przezroczysty, ale przyciski nie są. Tekst przycisku jest wyświetlany w obszarze mapy bitowe przycisków.

- **TBSTYLE_LIST** Umieszcza tekst przycisku z prawej strony Bitmap przycisków.

> [!NOTE]
> Aby zapobiec problemom z odświeżaniem, należy ustawić **TBSTYLE_FLAT** i **TBSTYLE_TRANSPARENT** style, zanim obiekt Toolbar będzie widoczny.

Poniższe Style określają, czy pasek narzędzi umożliwia użytkownikowi zmianę położenia poszczególnych przycisków w obiekcie Toolbar przy użyciu przeciągania i upuszczania:

- **TBSTYLE_ALTDRAG** Umożliwia użytkownikom zmianę położenia przycisku paska narzędzi, przeciągając go przy użyciu klawisza ALT. Jeśli ten styl nie zostanie określony, użytkownik musi trzymać wciśnięty klawisz SHIFT podczas przeciągania przycisku.

    > [!NOTE]
    >  Aby można było przeciągać przyciski paska narzędzi, należy określić styl **CCS_ADJUSTABLE** .

- **TBSTYLE_REGISTERDROP** Generuje **TBN_GETOBJECT** komunikatów powiadomień, aby zażądać obiektów docelowych upuszczania po przesunięciu wskaźnika myszy nad przyciskami paska narzędzi.

Pozostałe style mają wpływ na wizualizacje i Niewizualne aspekty obiektu Toolbar:

- **TBSTYLE_WRAPABLE** Tworzy pasek narzędzi, który może mieć wiele wierszy przycisków. Przyciski paska narzędzi mogą być zawijane do następnego wiersza, gdy pasek narzędzi zostanie zbyt wąski, aby uwzględnić wszystkie przyciski w tym samym wierszu. Zawijanie odbywa się na separacjach i niegrupach granic.

- **TBSTYLE_CUSTOMERASE** Generuje **NM_CUSTOMDRAW** komunikaty powiadomień podczas przetwarzania komunikatów **WM_ERASEBKGND** .

- **TBSTYLE_TOOLTIPS** Tworzy kontrolkę etykietki narzędzia, która może być używana przez aplikację do wyświetlania tekstu opisowego przycisków na pasku narzędzi.

Aby uzyskać pełną listę stylów paska narzędzi i stylów rozszerzonych, zapoznaj się z [kontrolkami paska narzędzi i stylów przycisków](/windows/win32/Controls/toolbar-control-and-button-styles) i [paskami narzędzi](/windows/win32/Controls/toolbar-extended-styles) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Formanty](controls-mfc.md)

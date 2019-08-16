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
ms.openlocfilehash: 590f0dce6c50ee6d0ca30c4c68e21787563bd686
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508731"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Dostosowywanie wyglądu formantu paska narzędzi

Klasa `CToolBarCtrl` zawiera wiele stylów, które wpływają na wygląd obiektu Toolbar (i, przez czas, zachowanie). Zmodyfikuj obiekt Toolbar przez ustawienie `dwCtrlStyle` parametru `CToolBarCtrl::Create` funkcji członkowskiej (lub `CToolBar::CreateEx`), gdy tworzysz najpierw formant Toolbar.

Następujące style mają wpływ na aspekt "3W" przycisków paska narzędzi oraz umieszczanie tekstu przycisku:

- **TBSTYLE_FLAT** Tworzy płaski pasek narzędzi, w którym zarówno pasek narzędzi, jak i przyciski są przezroczyste. Tekst przycisku jest wyświetlany w obszarze mapy bitowe przycisków. Gdy ten styl jest używany, przycisk poniżej kursora zostanie automatycznie wyróżniony.

- **TBSTYLE_TRANSPARENT** Tworzy przezroczysty pasek narzędzi. Na przezroczystym pasku narzędzi pasek narzędzi jest przezroczysty, ale przyciski nie są. Tekst przycisku jest wyświetlany w obszarze mapy bitowe przycisków.

- **TBSTYLE_LIST** Umieszcza tekst przycisku z prawej strony Bitmap przycisków.

> [!NOTE]
>  Aby zapobiec problemom z odświeżaniem, należy ustawić style **TBSTYLE_FLAT** i **TBSTYLE_TRANSPARENT** , zanim obiekt Toolbar będzie widoczny.

Poniższe Style określają, czy pasek narzędzi umożliwia użytkownikowi zmianę położenia poszczególnych przycisków w obiekcie Toolbar przy użyciu przeciągania i upuszczania:

- **TBSTYLE_ALTDRAG** Umożliwia użytkownikom zmianę położenia przycisku paska narzędzi, przeciągając go przy użyciu klawisza ALT. Jeśli ten styl nie zostanie określony, użytkownik musi trzymać wciśnięty klawisz SHIFT podczas przeciągania przycisku.

    > [!NOTE]
    >  Aby umożliwić przeciąganie przycisków paska narzędzi, należy określić styl **CCS_ADJUSTABLE** .

- **TBSTYLE_REGISTERDROP** Generuje komunikaty powiadomień **TBN_GETOBJECT** , aby zażądać obiektów docelowych upuszczania po przesunięciu wskaźnika myszy nad przyciskami paska narzędzi.

Pozostałe style mają wpływ na wizualizacje i Niewizualne aspekty obiektu Toolbar:

- **TBSTYLE_WRAPABLE** Tworzy pasek narzędzi, który może mieć wiele wierszy przycisków. Przyciski paska narzędzi mogą być zawijane do następnego wiersza, gdy pasek narzędzi zostanie zbyt wąski, aby uwzględnić wszystkie przyciski w tym samym wierszu. Zawijanie odbywa się na separacjach i niegrupach granic.

- **TBSTYLE_CUSTOMERASE** Generuje komunikaty powiadomień **NM_CUSTOMDRAW** podczas przetwarzania komunikatów **WM_ERASEBKGND** .

- **TBSTYLE_TOOLTIPS** Tworzy kontrolkę etykietki narzędzia, która może być używana przez aplikację do wyświetlania tekstu opisowego przycisków na pasku narzędzi.

Aby uzyskać pełną listę stylów paska narzędzi i stylów rozszerzonych, zapoznaj się z [kontrolkami paska narzędzi i stylów przycisków](/windows/win32/Controls/toolbar-control-and-button-styles) i [paskami narzędzi](/windows/win32/Controls/toolbar-extended-styles) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

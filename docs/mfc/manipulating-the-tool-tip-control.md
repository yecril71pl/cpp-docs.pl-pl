---
title: Operowanie formantem etykietki narzędzia
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
ms.openlocfilehash: d8c994748239871f17b878dd8ea7505a2a8a0b65
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279201"
---
# <a name="manipulating-the-tool-tip-control"></a>Operowanie formantem etykietki narzędzia

Klasa `CToolTipCtrl` udostępnia funkcje, które kontrolują różne atrybuty elementu członkowskiego grupy `CToolTipCtrl` obiektu i okno porad narzędzia.

Początkowy, w oknie podręcznym, a reshow czasów trwania dla narzędzia windows Porada można ustawić i pobierany za pomocą wywołania [GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime) i [SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime).

Zmień wygląd okna narzędzi tip z następujących funkcji:

- [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin) i [SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin) pobiera i ustawia odstęp między obramowanie Porada narzędzia i narzędzia Tekst porady.

- [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth) i [SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth) pobiera i ustawia maksymalną szerokość narzędzie okno porad do.

- [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor) i [SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor) pobiera i ustawia kolor tła narzędzia okno porad do.

- [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor) i [SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor) pobiera i ustawia kolor tekstu w narzędziu okno porad do.

Aby formantem etykietki narzędzia otrzymywać powiadomienia o ważnych wiadomości, takie jak komunikaty WM_LBUTTONXXX musi przekazywać komunikaty do Twojego firmant narzędzia wskazówki. Najlepszą metodę dla tej usługi relay jest zapewnienie wywołanie [CToolTipCtrl::RelayEvent](../mfc/reference/ctooltipctrl-class.md#relayevent)w `PreTranslateMessage` funkcja okno właściciela. Poniższy przykład przedstawia jedną z możliwych metod (zakładając, że formantem etykietki narzędzia jest nazywany `m_ToolTip`):

[!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]

Aby natychmiast usunąć okno porad narzędzie, należy wywołać [Pop](../mfc/reference/ctooltipctrl-class.md#pop) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

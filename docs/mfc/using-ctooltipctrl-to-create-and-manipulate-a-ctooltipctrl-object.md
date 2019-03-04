---
title: Używanie formantu CToolTipCtrl do tworzenia obiektu CToolTipCtrl i operowania nim
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: b0f008c70eeb43455408e5b0ad302df6b923608e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261209"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>Używanie formantu CToolTipCtrl do tworzenia obiektu CToolTipCtrl i operowania nim

Oto przykład [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) użycia:

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>Do tworzenia i manipulowania CToolTipCtrl

1. Konstruowania `CToolTipCtrl` obiektu.

1. Wywołaj [Utwórz](../mfc/reference/ctooltipctrl-class.md#create) Aby utworzyć wspólne formantem etykietki narzędzia Windows i dołączyć go do `CToolTipCtrl` obiektu.

1. Wywołaj [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) zarejestrować narzędzia z formantem etykietki narzędzia, aby informacje przechowywane w etykietce narzędzia jest wyświetlana, gdy kursor znajduje się w narzędziu.

1. Wywołaj [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) można ustawić informacji, zawierającą etykietka narzędzia.

1. Wywołaj [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) można ustawić nowy prostokąt otaczający narzędzia.

1. Wywołaj [hitTest —](../mfc/reference/ctooltipctrl-class.md#hittest) do testowania wskaż określają, czy znajduje się on w prostokąt otaczający danego narzędzia, a jeśli tak, można pobrać informacji o narzędziu.

1. Wywołaj [GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) można pobrać liczby narzędzi zarejestrowany z formantem etykietki narzędzia.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

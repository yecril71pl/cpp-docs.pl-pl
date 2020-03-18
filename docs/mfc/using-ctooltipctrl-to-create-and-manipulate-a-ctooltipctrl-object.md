---
title: Używanie formantu CToolTipCtrl do tworzenia obiektu CToolTipCtrl i operowania nim
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: 37dc7bc5a411ebab3737b87fd6977b26cff68178
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442222"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>Używanie formantu CToolTipCtrl do tworzenia obiektu CToolTipCtrl i operowania nim

Oto przykład użycia [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) :

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>Tworzenie i manipulowanie CToolTipCtrl

1. Konstruowanie obiektu `CToolTipCtrl`.

1. Wywołanie [Create](../mfc/reference/ctooltipctrl-class.md#create) w celu utworzenia typowej kontrolki narzędzia systemu Windows i dołączenie jej do obiektu `CToolTipCtrl`.

1. Wywołaj [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) , aby zarejestrować narzędzie za pomocą kontrolki etykietki narzędzia, tak aby informacje przechowywane w etykietce narzędzia były wyświetlane po umieszczeniu kursora w narzędziu.

1. Wywołaj [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) , aby ustawić informacje, które są przechowywane w etykietce narzędzia dla narzędzia.

1. Wywołaj [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) , aby ustawić nowy prostokąt ograniczający dla narzędzia.

1. Wywołaj [HitTest](../mfc/reference/ctooltipctrl-class.md#hittest) w celu przetestowania punktu, aby określić, czy znajduje się on w obrębie obwiedni danego narzędzia, a jeśli tak, Pobierz informacje o narzędziu.

1. Wywołaj [GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) , aby pobrać liczbę narzędzi zarejestrowanych w kontrolce etykietki narzędzia.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

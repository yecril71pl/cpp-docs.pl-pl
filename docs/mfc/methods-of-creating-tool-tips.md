---
title: Metody tworzenia etykietek narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
ms.openlocfilehash: 26f31705068df009e906d50451efa9ea6572d7e6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625457"
---
# <a name="methods-of-creating-tool-tips"></a>Metody tworzenia etykietek narzędzi

MFC oferuje trzy klasy do tworzenia kontrolki etykietki narzędzia i zarządzania nią: [CWnd](reference/cwnd-class.md), [CToolBarCtrl](reference/ctoolbarctrl-class.md), [CToolTipCtrl](reference/ctooltipctrl-class.md) i [CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md). Funkcje składowe etykietki narzędzia w tych klasach otaczają interfejs API wspólnego sterowania systemu Windows. Klasa `CToolBarCtrl` i Klasa pochodzą `CToolTipCtrl` od klasy `CWnd` .

`CWnd`Program udostępnia cztery funkcje składowe umożliwiające tworzenie etykietek narzędzi i zarządzanie nimi: [EnableToolTips](reference/cwnd-class.md#enabletooltips), [CancelToolTips](reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](reference/cwnd-class.md#filtertooltipmessage)i [OnToolHitTest](reference/cwnd-class.md#ontoolhittest). Zobacz te pojedyncze funkcje członkowskie, aby uzyskać więcej informacji na temat implementowania etykietek narzędzi.

Jeśli tworzysz pasek narzędzi przy użyciu `CToolBarCtrl` , możesz zaimplementować wskazówki dotyczące narzędzia dla tego paska narzędzi bezpośrednio przy użyciu następujących funkcji składowych: [GetToolTips](reference/ctoolbarctrl-class.md#gettooltips) i [SetToolTips](reference/ctoolbarctrl-class.md#settooltips). Aby uzyskać więcej informacji na temat sposobu implementowania etykietek narzędzi, zobacz te pojedyncze funkcje członkowskie i [Obsługa powiadomień etykietki narzędzi](handling-tool-tip-notifications.md) .

`CToolTipCtrl`Klasa oferuje funkcje formantu etykietki narzędzia typowego dla systemu Windows. Pojedyncza kontrolka etykietka narzędzia zawiera informacje dla więcej niż jednego narzędzia. Narzędzie to okno, takie jak okno podrzędne lub kontrolka, lub prostokątny obszar zdefiniowany przez aplikację w obszarze klienta okna. Klasa [CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md) dziedziczy z `CToolTipCtrl` i udostępnia dodatkowe style i funkcje wizualne.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolTipCtrl](using-ctooltipctrl.md)<br/>
[Formanty](controls-mfc.md)

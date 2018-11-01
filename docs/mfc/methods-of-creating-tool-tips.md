---
title: Metody tworzenia etykietek narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
ms.openlocfilehash: 80c826b3c9a4f9e24ebd201eaa9d775f9ad9f8cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663817"
---
# <a name="methods-of-creating-tool-tips"></a>Metody tworzenia etykietek narzędzi

Biblioteka MFC zawiera trzy klasy, tworzenie i zarządzanie nimi narzędzie formantu etykietki: [CWnd](../mfc/reference/cwnd-class.md), [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md), [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) i [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md). Funkcje elementów członkowskich Porada narzędzia w ramach tych zajęć opakować Windows formantu typowego interfejsu API. Klasa `CToolBarCtrl` i klasa `CToolTipCtrl` pochodzą z klasy `CWnd`.

`CWnd` dostarcza cztery funkcji elementów członkowskich, tworzenie i zarządzanie nimi etykietek narzędzi: [EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips), [CancelToolTips](../mfc/reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](../mfc/reference/cwnd-class.md#filtertooltipmessage), i [ontoolhittest — ](../mfc/reference/cwnd-class.md#ontoolhittest). Zobacz te funkcje poszczególnych elementów członkowskich, aby uzyskać więcej informacji na temat sposobu wdrażania etykietek narzędzi.

Jeśli utworzysz przy użyciu narzędzi `CToolBarCtrl`, można zaimplementować etykietki narzędzia dla tego paska narzędzi bezpośrednio przy użyciu następujących funkcji elementów członkowskich: [GetToolTips](../mfc/reference/ctoolbarctrl-class.md#gettooltips) i [SetToolTips](../mfc/reference/ctoolbarctrl-class.md#settooltips). Zobacz te funkcje poszczególnych elementów członkowskich i [Obsługa powiadomień dotyczących Porada narzędzi](../mfc/handling-tool-tip-notifications.md) Aby uzyskać więcej informacji na temat sposobu wdrażania etykietek narzędzi.

`CToolTipCtrl` Klasa oferuje funkcje wspólne formantem etykietki narzędzia Windows. Pojedynczy firmant narzędzia wskazówki może dostarczyć informacji dla więcej niż jednego narzędzia. To narzędzie jest albo okien, na przykład okno podrzędne lub kontroli lub zdefiniowanych przez aplikację prostokątny obszar w obrębie obszaru klienckiego okna. [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md) klasa pochodzi od `CToolTipCtrl` i udostępnia dodatkowe style wizualne i funkcje.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)


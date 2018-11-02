---
title: Ustawienia formantu etykietki narzędzia
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
ms.openlocfilehash: 99ad8b30599b4399e4574dea611991b4c8e1a8e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532681"
---
# <a name="settings-for-the-tool-tip-control"></a>Ustawienia formantu etykietki narzędzia

Możesz ustawić formantem etykietki narzędzia ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) jako aktywną lub nieaktywną. Po ustawieniu go jako aktywny formantem etykietki narzędzia jest wyświetlany, gdy kursor znajduje się nad narzędziem. Po ustawieniu go jako nieaktywne formantem etykietki narzędzia jest niewidoczny, nawet jeśli kursor znajduje się nad narzędziem. Wywołaj [Aktywuj](../mfc/reference/ctooltipctrl-class.md#activate) aby aktywować lub dezaktywować formantem etykietki narzędzia.

Można ustawić aktywny podpowiedzi do wyświetlenia etykietki narzędzia, gdy kursor znajduje się nad narzędziem, czy okno właściciela formantem etykietki narzędzia jest aktywne lub nieaktywne, przy użyciu stylu TTS_ALWAYSTIP. Jeśli nie używasz ten styl, formantem etykietki narzędzia pojawia się, gdy okno właściciela tego narzędzia jest aktywna, ale nie w przypadku, gdy jest nieaktywny.

Większość aplikacji zawiera pasków narzędzi za pomocą narzędzi, które odnoszą się do poleceń menu. Dla tych narzędzi jest wygodne formantem etykietki narzędzia wyświetlić ten sam tekst jako odpowiedniego elementu menu. System automatycznie usuwa handlowe "i" (&) akceleratora znaków z wszystkie ciągi przekazywane do formantem etykietki narzędzia, chyba, że kontrolka ma styl TTS_NOPREFIX.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

